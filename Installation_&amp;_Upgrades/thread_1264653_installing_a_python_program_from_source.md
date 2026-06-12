---
title: "installing a python program from source?"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by bruceschaller on 2009-09-12
Hi there,

I'm a chemical engineer and I often need to solve differential equations.  I've found an interesting piece of software called PyDDE.  I tried following their instructions.

I downloaded the source (the only way it is distributed), and followed the instructions in the install.txt file...

```
python setup.py install
```

and I get this:

........it's long...

running install
running build
running build_py
running build_ext
building 'PyDDE.ddesolve' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c PyDDE/src/wrapper.c -o build/temp.linux-x86_64-2.6/PyDDE/src/wrapper.o 
gcc: : No such file or directory
PyDDE/src/wrapper.c:7:20: error: Python.h: No such file or directory
In file included from /usr/include/python2.6/numpy/ndarrayobject.h:61,
                 from /usr/include/python2.6/numpy/arrayobject.h:14,
                 from PyDDE/src/wrapper.c:17:
/usr/include/python2.6/numpy/npy_common.h:71:2: error: #error Must use Python with unicode enabled.
In file included from /usr/include/python2.6/numpy/arrayobject.h:14,
                 from PyDDE/src/wrapper.c:17:
/usr/include/python2.6/numpy/ndarrayobject.h:181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:182: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘npy_uintp’
/usr/include/python2.6/numpy/ndarrayobject.h:284: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/python2.6/numpy/ndarrayobject.h:285: error: expected ‘)’ before ‘*’ token
/usr/include/python2.6/numpy/ndarrayobject.h:287: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:287: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:288: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:298: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:298: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:300: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:300: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:301: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:303: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:313: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:315: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:316: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:316: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:318: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:322: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:324: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:325: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:326: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:327: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:327: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:328: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:328: error: expected declaration specifiers or ‘...’ before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:332: error: expected specifier-qualifier-list before ‘npy_intp’
/usr/include/python2.6/numpy/ndarrayobject.h:345: error: expected specifier-qualifier-list before ‘PyArray_GetItemFunc’
/usr/include/python2.6/numpy/ndarrayobject.h:446: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:478: error: expected specifier-qualifier-list before ‘PyObject’
/usr/include/python2.6/numpy/ndarrayobject.h:488: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:513: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:521: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:528: error: expected declaration specifiers or ‘...’ before ‘PyObject’
/usr/include/python2.6/numpy/ndarrayobject.h:670: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:817: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:871: error: expected specifier-qualifier-list before ‘PyObject_HEAD’
/usr/include/python2.6/numpy/ndarrayobject.h:1084: error: expected specifier-qualifier-list before ‘npy_intp’
In file included from /usr/include/python2.6/numpy/ndarrayobject.h:1099,
                 from /usr/include/python2.6/numpy/arrayobject.h:14,
                 from PyDDE/src/wrapper.c:17:
/usr/include/python2.6/numpy/__multiarray_api.h: In function ‘_import_array’:
/usr/include/python2.6/numpy/__multiarray_api.h:971: error: ‘PyObject’ undeclared (first use in this function)
/usr/include/python2.6/numpy/__multiarray_api.h:971: error: (Each undeclared identifier is reported only once
/usr/include/python2.6/numpy/__multiarray_api.h:971: error: for each function it appears in.)
/usr/include/python2.6/numpy/__multiarray_api.h:971: error: ‘numpy’ undeclared (first use in this function)
/usr/include/python2.6/numpy/__multiarray_api.h:971: warning: implicit declaration of function ‘PyImport_ImportModule’
/usr/include/python2.6/numpy/__multiarray_api.h:972: error: ‘c_api’ undeclared (first use in this function)
/usr/include/python2.6/numpy/__multiarray_api.h:974: warning: implicit declaration of function ‘PyObject_GetAttrString’
/usr/include/python2.6/numpy/__multiarray_api.h:975: warning: implicit declaration of function ‘Py_DECREF’
/usr/include/python2.6/numpy/__multiarray_api.h:976: warning: implicit declaration of function ‘PyCObject_Check’
/usr/include/python2.6/numpy/__multiarray_api.h:977: warning: implicit declaration of function ‘PyCObject_AsVoidPtr’
/usr/include/python2.6/numpy/__multiarray_api.h:977: warning: cast to pointer from integer of different size
/usr/include/python2.6/numpy/__multiarray_api.h:984: warning: implicit declaration of function ‘PyErr_Format’
/usr/include/python2.6/numpy/__multiarray_api.h:984: error: ‘PyExc_RuntimeError’ undeclared (first use in this function)
PyDDE/src/wrapper.c: At top level:
PyDDE/src/wrapper.c:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:34: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:57: error: expected ‘)’ before ‘*’ token
PyDDE/src/wrapper.c:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:109: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:132: error: expected ‘)’ before ‘*’ token
PyDDE/src/wrapper.c:159: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:191: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PyDDE/src/wrapper.c: In function ‘switchfunctions’:
PyDDE/src/wrapper.c:340: error: ‘PyObject’ undeclared (first use in this function)
PyDDE/src/wrapper.c:340: error: ‘result’ undeclared (first use in this function)
PyDDE/src/wrapper.c:340: error: ‘arglist’ undeclared (first use in this function)
PyDDE/src/wrapper.c:340: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:341: error: ‘sPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:341: error: ‘cPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:341: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:348: warning: implicit declaration of function ‘pyArray_from_DblArray’
PyDDE/src/wrapper.c:352: warning: implicit declaration of function ‘Py_BuildValue’
PyDDE/src/wrapper.c:355: warning: implicit declaration of function ‘PyEval_CallObject’
PyDDE/src/wrapper.c:355: error: ‘switchfunctions_func’ undeclared (first use in this function)
PyDDE/src/wrapper.c:356: warning: implicit declaration of function ‘dblArray_from_PyArray’
PyDDE/src/wrapper.c:356: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c:362: warning: implicit declaration of function ‘Py_XDECREF’
PyDDE/src/wrapper.c:367: warning: implicit declaration of function ‘free’
PyDDE/src/wrapper.c:367: warning: incompatible implicit declaration of built-in function ‘free’
PyDDE/src/wrapper.c: In function ‘map’:
PyDDE/src/wrapper.c:380: error: ‘PyObject’ undeclared (first use in this function)
PyDDE/src/wrapper.c:380: error: ‘result’ undeclared (first use in this function)
PyDDE/src/wrapper.c:380: error: ‘arglist’ undeclared (first use in this function)
PyDDE/src/wrapper.c:380: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:381: error: ‘sPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:381: error: ‘cPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:381: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:381: error: ‘snewPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:381: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:381: error: ‘cnewPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:381: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:392: error: ‘map_func’ undeclared (first use in this function)
PyDDE/src/wrapper.c:394: warning: implicit declaration of function ‘PyArg_ParseTuple’
PyDDE/src/wrapper.c:395: warning: implicit declaration of function ‘PyErr_SetString’
PyDDE/src/wrapper.c:395: error: ‘PyExc_TypeError’ undeclared (first use in this function)
PyDDE/src/wrapper.c:404: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c:409: warning: incompatible implicit declaration of built-in function ‘free’
PyDDE/src/wrapper.c:410: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c: In function ‘grad’:
PyDDE/src/wrapper.c:441: error: ‘PyObject’ undeclared (first use in this function)
PyDDE/src/wrapper.c:441: error: ‘result’ undeclared (first use in this function)
PyDDE/src/wrapper.c:441: error: ‘arglist’ undeclared (first use in this function)
PyDDE/src/wrapper.c:441: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:442: error: ‘sPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:442: error: ‘cPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:442: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:462: error: ‘grad_func’ undeclared (first use in this function)
PyDDE/src/wrapper.c:467: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c:479: warning: incompatible implicit declaration of built-in function ‘free’
PyDDE/src/wrapper.c: In function ‘storehistory’:
PyDDE/src/wrapper.c:491: error: ‘PyObject’ undeclared (first use in this function)
PyDDE/src/wrapper.c:491: error: ‘result’ undeclared (first use in this function)
PyDDE/src/wrapper.c:491: error: ‘arglist’ undeclared (first use in this function)
PyDDE/src/wrapper.c:491: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:492: error: ‘sPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:492: error: ‘cPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:492: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:492: error: ‘gPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:492: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:493: error: ‘hisPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:493: error: ‘ghisPy’ undeclared (first use in this function)
PyDDE/src/wrapper.c:493: warning: left-hand operand of comma expression has no effect
PyDDE/src/wrapper.c:505: error: ‘storehistory_func’ undeclared (first use in this function)
PyDDE/src/wrapper.c:507: error: ‘PyExc_TypeError’ undeclared (first use in this function)
PyDDE/src/wrapper.c:517: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c:522: warning: incompatible implicit declaration of built-in function ‘free’
PyDDE/src/wrapper.c:524: warning: assignment makes pointer from integer without a cast
PyDDE/src/wrapper.c: At top level:
PyDDE/src/wrapper.c:548: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ddesolveMethods’
PyDDE/src/wrapper.c: In function ‘initddesolve’:
PyDDE/src/wrapper.c:558: error: ‘PyObject’ undeclared (first use in this function)
PyDDE/src/wrapper.c:558: error: ‘m’ undeclared (first use in this function)
PyDDE/src/wrapper.c:559: warning: implicit declaration of function ‘Py_InitModule’
PyDDE/src/wrapper.c:559: error: ‘ddesolveMethods’ undeclared (first use in this function)
PyDDE/src/wrapper.c:560: warning: implicit declaration of function ‘PyErr_Print’
PyDDE/src/wrapper.c:560: error: ‘PyExc_ImportError’ undeclared (first use in this function)
error: command 'gcc' failed with exit status 1

--------------------------------------------------------------

At the very beginning it said gcc: No such file or directory...
But I do have GCC installed.  

Any help would be much appreciated.

Bruce Schaller

---

### Post by unutbu on 2009-09-12
```

PyDDE/src/wrapper.c:7:20: error: **Python.h: No such file or directory**
```

Using the search facility at [http://packages.ubuntu.com](http://packages.ubuntu.com) it appears Python.h is provided by python2.6-dev. Maybe check to make sure you have the python2.6-dev package installed.

(See [http://packages.ubuntu.com/search?searchon=contents&keywords=Python.h&mode=&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=Python.h&mode=&suite=jaunty&arch=any))

---

### Post by bruceschaller on 2009-09-12
Hi There!

Thanks so much for the help!  Their documentation only mentioned having python installed, not any dev packages.  

Bruce

---

