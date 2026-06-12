---
title: "bug ? missing /usr/X11R6/lib/modules/dri/i830_dri.so in xlibmesa-dri?"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by rdxinet on 2005-03-28
I have an  Intel Corp. 82865G Integrated Graphics Device it seem it uses the i830.ko kernel module and /usr/X11R6/lib/modules/dri/i830_dri.so but the xlibmesa-dri package does not contain this file.

when I do:
 LIBGL_DEBUG=1 glxinfo
...
libGL error: dlopen /usr/X11R6/lib/modules/dri/i830_dri.so failed (/usr/X11R6/lib/modules/dri/i830_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: i830_dri.so
display: :0  screen: 0
direct rendering: No
...

And I have not dri in Hoary in a x86 box.

---

### Post by daniels on 2005-03-28
Only if you're using xserver-xfree86 -- xorg uses the i915 kernel module (yes, for i830-based chipsets, like my i855), and i915_dri.so.

---

### Post by rdxinet on 2005-03-28
I have "dist-upgraded" from a warty, I think i'm using xorg.

---

### Post by daniels on 2005-03-28
Only if you keep the 'ubuntu-desktop' package installed.

---

### Post by rdxinet on 2005-03-29
I have installed ubuntu-desktop and kernel image 2.6.10 and now i have the dri enabled, thanks a lot :)

but, I've lost the mode 1600x1200@85Hz that I used with Xfree. Now i can use 1600x1200@75Hz only. The Vsyn and Hsyn are ok in the /etc/X11/xorg.conf and I've tried with a lot of ModeLines.

some ideas?

---

