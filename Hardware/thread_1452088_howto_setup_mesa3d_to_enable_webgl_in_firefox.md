---
title: "howto setup mesa3d to enable webgl in firefox?"
date: 2010-04-11
forum: Hardware
---

### Post by aljosa on 2010-04-11
my card (ubuntu lucid):
$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]

$ glxinfo |grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 1.5 Mesa 7.7.1

problem when i try to access webgl content with firefox:
Canvas 3D: creating PBuffer...
nsGLPbufferGLX: gActiveBuffers: 1
CANVAS3D FBCONFIG: 0 (nil)
Canvas 3D: No GLXFBConfig found
nsGLPbufferOSMESA: gActiveBuffers: 1
Can't find symbol 'OSMesaCreateContextExt'

Any ideas?

---

### Post by nayankk on 2010-05-03
I am also getting the same error,

Canvas 3D: creating PBuffer...
nsGLPbufferGLX: gActiveBuffers: 1
CANVAS3D FBCONFIG: 0 (nil)
Canvas 3D: No GLXFBConfig found
nsGLPbufferOSMESA: gActiveBuffers: 1
Can't find symbol 'OSMesaCreateContextExt'

---

