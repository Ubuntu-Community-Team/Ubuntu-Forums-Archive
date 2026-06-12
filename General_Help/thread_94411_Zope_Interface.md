---
title: "Zope Interface"
date: 2005-11-24
forum: General Help
---

### Post by souled on 2005-11-24
When I try to install Zope Interface using python setup.py build, I get this error. ```
running build
running build_py
running build_ext
building 'zope.interface._zope_interface_coptimizations' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPI C -IDependencies/zope.interface-ZopeInterface-3.0.1/zope.interface -I/usr/includ e/python2.4 -c Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_z ope_interface_coptimizations.c -o build/temp.linux-i686-2.4/Dependencies/zope.in terface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.o
unable to execute gcc: No such file or directory
error: command 'gcc' failed with exit status 1
```
I have gcc installed, but it seems like python is looking in the wrong place for it. Is there a way I can point python to the correct path to gcc?

---

### Post by souled on 2005-11-24
Ok, I installed build essential, but when i run the command to build, I now get this error:
```
running build
running build_py
running build_ext
building 'zope.interface._zope_interface_coptimizations' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -IDependencies/zope.interface-ZopeInterface-3.0.1/zope.interface -I/usr/include/python2.4 -c Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c -o build/temp.linux-i686-2.4/Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.o
Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c:339: error: static declaration of &#8216;SpecType&#8217; follows non-static declaration
Dependencies/zope.interface-ZopeInterface-3.0.1/zope.interface/_zope_interface_coptimizations.c:73: error: previous declaration of &#8216;SpecType&#8217; was here
error: command 'gcc' failed with exit status 1

```

Anyone have any ideas?

---

### Post by souled on 2005-11-24
Yay, fixed the problem. It seems the current stable release has some problem with gcc, so I downloaded the latest version and it installed perfectly.

---

