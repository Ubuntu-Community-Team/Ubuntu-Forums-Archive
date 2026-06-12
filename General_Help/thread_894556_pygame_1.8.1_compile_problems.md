---
title: "pygame 1.8.1 compile problems"
date: 2008-08-19
forum: General Help
---

### Post by Perk on 2008-08-19
I downloaded the source for pygame 1.8.1, downloaded the dependencies, and ran "sudo python setup.py". I got a bunch of errors:

No Arguments Given, Perform Default Install? [Y/n]y
running install
running build
running build_py
running build_ext
building 'pygame.imageext' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/include/SDL -I/usr/include/SDL -I/usr/include -I/usr/include -I/usr/include/python2.5 -c src/imageext.c -o build/temp.linux-i686-2.5/src/imageext.o
In file included from src/imageext.c:31:
src/pygame.h:60:20: error: Python.h: No such file or directory
In file included from src/imageext.c:31:
src/pygame.h:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lenfunc’
src/pygame.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeargfunc’
src/pygame.h:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizeobjargproc’
src/pygame.h:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeargfunc’
src/pygame.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssizessizeobjargproc’
src/pygame.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘readbufferproc’
src/pygame.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘writebufferproc’
src/pygame.h:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘segcountproc’
src/pygame.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘charbufferproc’
src/pygame.h:196: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:237: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:272: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:311: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:349: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:408: error: expected specifier-qualifier-list before ‘PyObject’
src/pygame.h:415: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:457: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/pygame.h:525: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
src/imageext.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/imageext.c:353: warning: function declaration isn’t a prototype
src/imageext.c: In function ‘opengltosdl’:
src/imageext.c:356: error: ‘PyObject’ undeclared (first use in this function)
src/imageext.c:356: error: (Each undeclared identifier is reported only once
src/imageext.c:356: error: for each function it appears in.)
src/imageext.c:356: error: ‘pyopengl’ undeclared (first use in this function)
src/imageext.c:356: error: ‘readpixels’ undeclared (first use in this function)
src/imageext.c:356: warning: left-hand operand of comma expression has no effect
src/imageext.c:372: warning: implicit declaration of function ‘PyErr_SetString’
src/imageext.c:372: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
src/imageext.c:372: error: expected expression before ‘)’ token
src/imageext.c:376: error: expected expression before ‘)’ token
src/imageext.c:383: error: ‘PyExc_MemoryError’ undeclared (first use in this function)
src/imageext.c:383: error: expected expression before ‘)’ token
src/imageext.c:403: error: expected expression before ‘)’ token
src/imageext.c:403: error: expected expression before ‘)’ token
src/imageext.c:357: warning: unused variable ‘formatflag’
src/imageext.c:357: warning: unused variable ‘typeflag’
src/imageext.c: At top level:
src/imageext.c:418: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
src/imageext.c:496: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘image_builtins’
src/imageext.c: In function ‘initimageext’:
src/imageext.c:507: warning: implicit declaration of function ‘Py_InitModule3’
src/imageext.c:507: error: ‘image_builtins’ undeclared (first use in this function)
src/imageext.c:510: error: ‘PyObject’ undeclared (first use in this function)
src/imageext.c:510: error: ‘_module’ undeclared (first use in this function)
src/imageext.c:510: warning: implicit declaration of function ‘PyImport_ImportModule’
src/imageext.c:510: error: ‘_dict’ undeclared (first use in this function)
src/imageext.c:510: warning: implicit declaration of function ‘PyModule_GetDict’
src/imageext.c:510: error: ‘_c_api’ undeclared (first use in this function)
src/imageext.c:510: warning: implicit declaration of function ‘PyDict_GetItemString’
src/imageext.c:510: warning: implicit declaration of function ‘PyCObject_Check’
src/imageext.c:510: warning: implicit declaration of function ‘PyCObject_AsVoidPtr’
src/imageext.c:510: warning: implicit declaration of function ‘Py_DECREF’
error: command 'gcc' failed with exit status 1


I'm not sure how to fix this. Anyone else running into the same problem?
I'm using python 2.5.2, gcc 4.2.3, and Ubuntu 8.04. Thanks!

---

### Post by illumen on 2008-08-20
You're missing some dependencies.

Details here:
[http://pygame.org/wiki/CompileUbuntu](http://pygame.org/wiki/CompileUbuntu)

cu,

---

