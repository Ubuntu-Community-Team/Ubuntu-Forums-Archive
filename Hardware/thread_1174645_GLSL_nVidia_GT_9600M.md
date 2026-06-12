---
title: "GLSL nVidia GT 9600M"
date: 2009-05-31
forum: Hardware
---

### Post by teodron on 2009-05-31
Hello,

I have tried to run some simple GLSL programs under Linux KUbuntu using the drivers from nVidia, but the result is either a segfault or a message that there is no GLSL support. I am using the lGLEW Wrangler extensions library. Since this is quite a new graphics card (after OpenGL 2.1 was released as a standard), it should support GLSL. If you have any experience regarding this issue (i.e. you suspect what should be further done to make things work), please reply to this thread! It's needless to say, but GLSL programming is of great importance for me and I'd be very grateful to you..

Best wishes..

---

### Post by teodron on 2009-06-10
I managed to make it work after I installed the Linux drivers from the nVidia website. I used the synaptic package manager to get the Wrangler Extenstion library support (GLEW) and the tutorial from lighthouse3d ([http://www.lighthouse3d.com/opengl/glsl/index.php?minimal](http://www.lighthouse3d.com/opengl/glsl/index.php?minimal)). The version for OpenGL2.0 works fine. After compiling the program with g++ source.cpp -o executable -lglut -lGLEW, the executable needs to be ran as super user (sudo). 
That's in case anybody else has the same problems that took me quite a lot to figure out.

---

