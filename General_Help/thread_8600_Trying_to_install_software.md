---
title: "Trying to install software"
date: 2004-12-19
forum: General Help
---

### Post by sgnlfive on 2004-12-19
Hey everyone I just found a neat fractal generator, that seems to be pretty popular. But I have no idea how to install it as I cannot find any information.

If anyone could help, that'd be great.

The software: Fract-o-Rama: [http://fractorama.com/](http://fractorama.com/)

danke :)

**dang it sorry i posted in the wrong forum :(

---

### Post by Johan on 2004-12-19
This will usually work: 
 1. Download the factorama.tar.gz file.
 2. Extract it with tar zxfv factorama.tar.gz
 3. Enter the new directory and..
 4. Type make && make install
 5 Run the program.

In most cases you will have to type ./configure before makeing but that doesn't seem to be the case this time.

---

### Post by sgnlfive on 2004-12-19
I gave it a try and it spit this out:

```
make -C lib/fractal "RELEASE="
make[1]: Entering directory `/home/mykel/fractorama/src/lib/fractal'
g++ -c -W -Wall  -g  -o GradientColorNode_debug.o GradientColorNode.cpp
In file included from /usr/include/c++/3.3/backward/iostream.h:31,
                 from ColorTable.h:4,
                 from ColorNode.h:4,
                 from GradientColorNode.h:4,
                 from GradientColorNode.cpp:1:
/usr/include/c++/3.3/backward/backward_warning.h:32:2: warning: #warning This fi le includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples in clude substituting the <X> header for the <X.h> header for C++ includes, or <sst ream> instead of the deprecated header <strstream.h>. To disable this warning us e -Wno-deprecated.
In file included from GradientColorNode.cpp:1:
GradientColorNode.h:21: error: type specifier omitted for parameter `strstream'
GradientColorNode.h:21: error: parse error before `&' token
GradientColorNode.cpp:5: error: type specifier omitted for parameter `strstream
   '
GradientColorNode.cpp:5: error: parse error before `&' token
GradientColorNode.cpp: In static member function `static GradientColorNode*
   GradientColorNode::create(...)':
GradientColorNode.cpp:8: error: `count' undeclared (first use this function)
GradientColorNode.cpp:8: error: (Each undeclared identifier is reported only
   once for each function it appears in.)
GradientColorNode.cpp:8: error: `size' undeclared (first use this function)
GradientColorNode.cpp:10: error: `errStream' undeclared (first use this
   function)
GradientColorNode.cpp:17: error: `theStack' undeclared (first use this
   function)
make[1]: *** [GradientColorNode_debug.o] Error 1
make[1]: Leaving directory `/home/mykel/fractorama/src/lib/fractal'
make: *** [build_libfractal] Error 2
mykel@wonderland:~/fractorama/src $ sudo make && make install
make -C lib/fractal "RELEASE="
make[1]: Entering directory `/home/mykel/fractorama/src/lib/fractal'
g++ -c -W -Wall  -g  -o GradientColorNode_debug.o GradientColorNode.cpp
In file included from /usr/include/c++/3.3/backward/iostream.h:31,
                 from ColorTable.h:4,
                 from ColorNode.h:4,
                 from GradientColorNode.h:4,
                 from GradientColorNode.cpp:1:
/usr/include/c++/3.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <sstream> instead of the deprecated header <strstream.h>. To disable this warning use -Wno-deprecated.
In file included from GradientColorNode.cpp:1:
GradientColorNode.h:21: error: type specifier omitted for parameter `strstream'
GradientColorNode.h:21: error: parse error before `&' token
GradientColorNode.cpp:5: error: type specifier omitted for parameter `strstream
   '
GradientColorNode.cpp:5: error: parse error before `&' token
GradientColorNode.cpp: In static member function `static GradientColorNode*
   GradientColorNode::create(...)':
GradientColorNode.cpp:8: error: `count' undeclared (first use this function)
GradientColorNode.cpp:8: error: (Each undeclared identifier is reported only
   once for each function it appears in.)
GradientColorNode.cpp:8: error: `size' undeclared (first use this function)
GradientColorNode.cpp:10: error: `errStream' undeclared (first use this
   function)
GradientColorNode.cpp:17: error: `theStack' undeclared (first use this
   function)
make[1]: *** [GradientColorNode_debug.o] Error 1
make[1]: Leaving directory `/home/mykel/fractorama/src/lib/fractal'
make: *** [build_libfractal] Error 2

```

Any clues?

---

