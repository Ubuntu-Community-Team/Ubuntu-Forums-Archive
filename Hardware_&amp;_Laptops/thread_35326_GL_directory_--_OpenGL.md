---
title: "GL directory -- OpenGL"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by ubuntuyajiv on 2005-05-18
hi all,

i am new to LINUX and installed ubuntu in my laptop. since it has nvidia geforce graphics card, i installed the nvidia driver too. now i've an application that links to usual GL header files (GL.h); in my application, itz included as GL/gl.h but when i compile it, it couldn't find the GL directory.

I had been using windows XP all the time and i could do directory search to find GL and move them correspondingly or set the PATH variable for the same. 

my questions are ::

a) when i install the nvidia driver, won't it setup a GL directory and put the header files onto it
b) how can i do a file search in linux similar to win XP file/directory search.
c) do i miss any other packages that need to be installed.

.yajiv

---

### Post by alastair on 2005-05-18
You might need to install either :

xlibmesa-gl-dev:

or perhaps (but this might be GLX .h files and libs only) :

nvidia-glx-dev

(I'm not sure what nvidia-glx-dev provides. Perhaps you can check)

---

