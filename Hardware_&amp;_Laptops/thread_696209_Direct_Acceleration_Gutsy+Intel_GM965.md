---
title: "Direct Acceleration: Gutsy+Intel GM965"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by alexstorer on 2008-02-13
Hey there, I'm not sure how to turn on direct rendering.  I've got all the mesa stuff installed (including the dri package) but I'm not sure how to enable it.

[FONT="Courier New"]storer@quoala:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
storer@quoala:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/FONT]

I can post my xorg.conf on request.

Thanks!

PS - glxgears crashes X when I run it, but compiz is running pretty much perfectly.

[Edit: this is addressed here, which seems to work.  [http://ubuntuforums.org/showthread.php?t=583081]](http://ubuntuforums.org/showthread.php?t=583081])

---

### Post by alexstorer on 2008-02-13
I guess since this is the laptop forum, i should say that this is a T61. :)

---

