---
title: "OpenGL 2.x on Sandy Bridge"
date: 2011-12-24
forum: Hardware
---

### Post by freedombono on 2011-12-24
I have a Sandy Bridge laptop with an Intel HD Graphics 3000 integrated graphics card, where I have Oneiric installed. If I run glxinfo on a terminal, I get that 

server glx version string: 1.4
client glx version string: 1.4

Shouln't this hardware lets me run OpenGL 2.x?? I know from Phoronix that the upstream Intel drivers are almost hitting OpenGL 3.0 compatibility, surely the Ubuntu drivers aren't *that* far behind upstream??..

---

### Post by Blaze33 on 2011-12-24
[GLX]("http://fr.wikipedia.org/wiki/GLX") isn't OpenGL.
I also have a SandyBridge laptop and get the following :

```
$ glxinfo|grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
**OpenGL version string: 2.1 Mesa 7.12-devel**
OpenGL shading language version string: 1.30

```

So, currently having OpenGL 2.1 and hopefully going for 3.0 soon ^^

---

### Post by freedombono on 2011-12-24
Oh, okay, I feel silly now xD

Still, though, what led me to check all this was trying to enable WebGL on GoogleMaps, and them telling me my hardware wasn't supported. Isn't OpenGL 2.0 all that's needed to run WebGL?

---

### Post by freedombono on 2011-12-25
So yeah, turns out the drivers were completely innocent. Took me ages to pin down, but turns down it was a single Firefox addon (!) breaking WebGL. Issue fixed.

---

