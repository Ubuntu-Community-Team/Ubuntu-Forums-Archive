---
title: "Need to upgrade OpenGL version"
date: 2018-01-16
forum: Hardware
---

### Post by faubes on 2018-01-16
Hello,

I'd like to do OpenGL development on my Dell XPS 13 running Ubunut 16.04 but apparently cannot get the right version of OpenGL to work.

A test program provided by the prof reports that OpenGL is version 3.0 but needs at least 3.3. My efforts at googleshooting have failed thus far.

I have the intel graphics driver tool installed and apparently have all the latest drivers.

Here's what glxinfo | grep OpenGL returns:

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 520 (Skylake GT2) 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:


Has anyone encountered this problem before? or have any idea how to solve it?

Many thanks!

---

### Post by Yellow Pasque on 2018-01-16
[https://askubuntu.com/questions/850900/why-is-my-opengl-version-stuck-at-3-0-despite-new-hardware-software](https://askubuntu.com/questions/850900/why-is-my-opengl-version-stuck-at-3-0-despite-new-hardware-software)

TL;DR version: Try launching you program like this -
```
MESA_GL_VERSION_OVERRIDE=4.5 MESA_GLSL_VERSION_OVERRIDE=450 programname
```

---

### Post by faubes on 2018-01-16
Thanks for your reply. 

I read the link you posted and did as you suggested to override the reported version and, well...

~/school/csi4130/code/lab0/bin$ MESA_GL_VERSION_OVERRIDE=4.5 MESA_GLSL_VERSION_OVERRIDE=450 ./triangle
Using GLEW 1.13.0
Running OpenGL 4.5
Segmentation fault (core dumped)

Now, I've successfully compiled and executed this program on a Windows machine, so I know the code should be ok. Any idea what might be causing this segfault?

Very peculiar.

---

### Post by Yellow Pasque on 2018-01-16
Try with MESA_GL_VERSION_OVERRIDE=3.3 MESA_GLSL_VERSION_OVERRIDE=330

Other than that, I'm out of ideas. Maybe if it's possible to link to the source, that could help. If it's legally questionable, don't do it.

---

### Post by faubes on 2018-01-16
Source here: [https://pastebin.com/UFrSMm0y](https://pastebin.com/UFrSMm0y)

Tempted to give up on this problem, work on the desktop instead.

---

