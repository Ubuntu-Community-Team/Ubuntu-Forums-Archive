---
title: "Opengl 4.1 on ATI 6470m"
date: 2016-06-25
forum: Hardware
---

### Post by fettuohi on 2016-06-25
I have a HP-EliteBook-8460p with ATI 6470m. According to the hardware the card haes OpenGL 4.1 support. But in Ubuntu 16.04 I get

andre@andre-HP-EliteBook-8460p:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 3.0 Mesa 12.1.0-devel (git-727a9b2 2016-06-25 xenial-oibaf-ppa)

I am using this ppa BTW

ppa:oibaf/graphics-drivers

under "About This Computer" it says under Graphics

Gallium 0.4 on AMD CAICOS (DRM 2.43.0 / 4.4.0-24-generic, LLVM 3.8.0)

I thought the mesa etc. had OpenGL 4.1 support now at least. Is there a way to get that with open source drivers on this card?

---

### Post by Yellow Pasque on 2016-06-25
> OpenGL version string: 3.0 Mesa 
That is the compatibility profile version. Check the core version:
```
glxinfo | grep string
```

[http://www.phoronix.com/image-viewer.php?id=2016&image=amd_cypress_gl41_lrg](http://www.phoronix.com/image-viewer.php?id=2016&image=amd_cypress_gl41_lrg)

---

### Post by fettuohi on 2016-06-26
> **Temüjin said:**
> That is the compatibility profile version. Check the core version:
```
glxinfo | grep string
```

[http://www.phoronix.com/image-viewer.php?id=2016&image=amd_cypress_gl41_lrg](http://www.phoronix.com/image-viewer.php?id=2016&image=amd_cypress_gl41_lrg)

```

andre@andre-HP-EliteBook-8460p:~$ glxinfo | grep string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD CAICOS (DRM 2.43.0 / 4.4.0-24-generic, LLVM 3.8.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.1.0-devel (git-81978c6 2016-06-25 xenial-oibaf-ppa)
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 12.1.0-devel (git-81978c6 2016-06-25 xenial-oibaf-ppa)
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.1.0-devel (git-81978c6 2016-06-25 xenial-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

```

---

