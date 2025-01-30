---
layout: post
title: Fix Angular compatibility issue
subtitle: Fix the error - this likely means that the library which declares ThemesModule is not compatible with Angular Ivy
gh-repo: shafi-/shafi
gh-badge: [star, fork, follow]
tags: [tips, tricks, angular, frontend]
comments: true
author: Md Abdullahil Shafi
---

## The issue

Have you ever encountered an error like this:
*This likely means that the library [library] which declares **XModule** is not compatible with Angular Ivy*

## How to fix
Add `"postinstall": "ngcc"` to your `package.json` and run `npm install`.

```json
{
    "scripts": {
        "postinstall": "ngcc"
    }
}
```

Also if you can run `npm run postinstall` directly.

<br>

## Explanation:
`ngcc` stands for **"Angular Compatibility Compiler"**. It's a tool provided by the Angular team to help with compatibility issues between different versions of Angular and third-party libraries.

When you run `ngcc`, it compiles and updates the metadata of third-party libraries to make them compatible with the current version of Angular. This is necessary because Angular uses a metadata system to keep track of components, services, and other dependencies, and this metadata needs to be in a specific format.

## More details:
Here's what ngcc does:

Scans for incompatible libraries: ngcc searches for third-party libraries that are not compatible with the current version of Angular.
Compiles and updates metadata: For each incompatible library, ngcc compiles the library's code and updates its metadata to match the expected format.
Generates new metadata files: ngcc generates new metadata files for the updated libraries, which are then used by Angular to resolve dependencies.
By running ngcc, you ensured that the DatadogModule was properly compiled and updated to be compatible with your version of Angular, which resolved the error.

## Conclusion:
It's worth noting that ngcc is usually run automatically by the Angular CLI when you install or update dependencies. However, in some cases, you may need to run it manually to resolve compatibility issues.

