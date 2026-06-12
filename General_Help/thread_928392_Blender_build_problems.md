---
title: "Blender build problems"
date: 2008-09-23
forum: General Help
---

### Post by jolly194 on 2008-09-23
I tried going to Blender.org for help, but I tried registering twice and both times never got the necessary email to finish the registration, so I'm hoping someone here can help me. I'm taking a software engineering class and our first assignment was to download an open source project and build it from scratch. I've never tried building more than a simple C++ program before. I'm using Hardy Heron and trying to build Blender with scons. I've run into a problem where it appears that it is looking for png.h header file. I have the png.h header file in the location it is giving me the error for, so I'm lost.  Here's a portion of the build where the errors start appearing. Can any one help me out on this? If needed, I can re-post with the entire list of error messages, but I figured this was a good start.


Compiling ==> 'utilities.cpp'
intern/elbeem/intern/utilities.cpp:28:17: error: png.h: No such file or directory
intern/elbeem/intern/utilities.cpp: In function ‘int writePng(const char*, unsigned char**, int, int)’:
intern/elbeem/intern/utilities.cpp:134: error: ‘PNG_COLOR_TYPE_RGBA’ was not declared in this scope
intern/elbeem/intern/utilities.cpp:136: error: ‘png_structp’ was not declared in this scope
intern/elbeem/intern/utilities.cpp:136: error: expected `;' before ‘png_ptr’
intern/elbeem/intern/utilities.cpp:137: error: ‘png_infop’ was not declared in this scope
intern/elbeem/intern/utilities.cpp:137: error: expected `;' before ‘info_ptr’

---

### Post by ellgor on 2008-09-24
Hi,

It looks like it is looking for a dev package, something like "libpng.dev" check to see if this is the case, and, if more similar errors occur with other things then dev them too.

Regards, Ellgor.

---

### Post by jolly194 on 2008-09-24
Yup, that was what I needed. Thanks much!

---

