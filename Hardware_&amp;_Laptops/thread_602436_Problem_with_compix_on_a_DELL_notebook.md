---
title: "Problem with compix on a DELL notebook"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by bach on 2007-11-04
I am running Ubuntu 7.10 on a DELL D630 notebook. I am using the compiz visual effects. I have direct rendering:

cribari@jsbach:~$ glxinfo | grep direct
direct rendering: Yes

I do not have xserver-xgl installed; libgl1-mesa-dri and libgl1-mesa-glx are installed. 

I am having problems with movie viewers such as xine and vlc (they do not work at all). For instance, when I try to start xine I get:

cribari@jsbach:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2470
  Current serial number in output stream:  2471
cribari@jsbach:~$ 

The program fails to start. 

The problem disappears when the compiz visual effects are disabled. 

Suggestions are welcome. Thanks in advance.

---

