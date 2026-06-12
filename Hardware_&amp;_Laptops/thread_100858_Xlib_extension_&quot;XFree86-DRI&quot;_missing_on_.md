---
title: "Xlib: extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;."
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by thespinesplitter on 2005-12-08
well thats it, someone posted to me that theres a symlink that i should check, except he copied and pasted from from another post that was dealing with Nvidia and not ATI, im still rather noobish but how do i know where does the libGL.so.1  symlink point to and how do i find the other libGL and make sure its the ATI one and not the MESA one

>  Jule Slootbeek wrote:

Debian-users,

another something i've been trying to figure out for a while.
I have a nVidia GeForce MX 420 running the latest drivers, but whenever i try to run a opengl prog, like glxgears i get this:

jule@dolphy:~$ glxgears
Xlib: extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).



Make sure that the libGL.so.1 symlink in /usr/X11R6/lib
points to the real libGL.so.1.2 from nVidia (not the one
from the xlibs-mesa package). I have had this happen to
me (though with the ATI drivers instead of nVidia) when
OpenGL apps would stop working after that symlink disappeared.


-Roberto Sanchez

---

### Post by thespinesplitter on 2005-12-09
bump! bump!

---

