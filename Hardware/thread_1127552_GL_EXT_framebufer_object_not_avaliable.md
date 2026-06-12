---
title: "GL_EXT_framebufer_object not avaliable?"
date: 2009-04-16
forum: Hardware
---

### Post by rob356 on 2009-04-16
So I have been trying to get the Dolphin gamecube emulator to work. When it runs it spits out this error, and promply Seg faults 
```
Need GL_EXT_framebufer_object, does you graphics card support OpenGL 2.x?
```
I have an ATI Radeon X1300 (R500), I am also running Ubuntu 9.04(I know it is still a beta, but wait one sec ;)) I have dug up that ATI(AMD) has stopped supporting up to the R500 chipset in the latest version of fglrx, which is necessary for compatibility with Xorg 1.6, which Jaunty ships with. (Will ATI ever build in support for the R500 again, or is it gone forever?) So I am using the open radeon drivers, 3D and everything works, but I wanted to know if the "GL_EXT_framebufer_object" OpenGL command was supported by them or if I was just going crazy and doing something stupid.:P
Thanks

---

