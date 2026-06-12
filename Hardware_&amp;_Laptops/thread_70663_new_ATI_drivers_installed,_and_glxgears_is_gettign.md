---
title: "new ATI drivers installed, and glxgears is gettign 500 fps :("
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2005-09-30
i've just installed the new ATI drivers, for my radeon 9700 (laptop).  the installation went fine, and i think the drivers are loaded.  i've used fglrxconfig to generate an xorg.conf file, which is working.

the problem is that when i run glxgears i only get ~500 fps, so something ain't working!

simon@ahimsa:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

simon@ahimsa:~$ dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 7454 using kernel context 0
[fglrx:firegl_unlock] *ERROR* Process 9994 using kernel context 0

simon@ahimsa:~$ cat /etc/X11/xorg.conf | grep Driver
    Driver      "kbd"
    Driver "mouse"
#    Driver      "mouse"
#    Driver     "magellan"
#    Driver     "spaceorb"
#    Driver     "microtouch"
#    Driver     "elo2300"
# The Driver line must be present.  When using run-time loadable driver
    Driver      "vga"
    Driver                              "fglrx"


should i also include my xorg.conf file?

i think the line "OpenGL vendor string: Mesa project: www.mesa3d.org" says it all--it's not loading the ati drivers, and i've no idea why.

any help will be much appreciated!  (i need to be working in maya quite soon...)

thanks,
Simon

---

### Post by mlomker on 2005-09-30
> [fglrx:firegl_unlock] *ERROR* Process 7454 using kernel context 0


A couple individuals have seen this before and for the last person it was because he didn't delete the /lib/modules/*yourkernelversion*/kernel/drivers/char/drm/fglrx.ko file prior to the installation.  

I'm assuming that you followed my [how-to.]("http://www.ubuntuforums.org/showthread.php?p=348911")  I'd recommend running through it again and being careful to delete everything with **fglrx** in its name.

If it's any consolation, I spent an entire day getting mine installed the first time.

---

### Post by eduard0 on 2005-10-01
Or you can just simply edit /lib/modules/<kernelversionhere>/modules.dep
Replace all (I had 2) /lib/modules/yourkernelversion/kernel/drivers/char/drm/fglrx.ko with /lib/modules/fglrx/fglrx.ko

Of course, remember to backup the file first.

---

### Post by mlomker on 2005-10-01
[QUOTE=eduard0]Or you can just simply edit /lib/modules/<kernelversionhere>/modules.dep
[/QUOTE]

That should never be necessary unless your install failed.  Their .sh script runs **depmod -A** at the end, which automatically rebuilds the modules.dep...as far as I know.

---

### Post by eduard0 on 2005-10-01
Well, ATI Driver Installation didn't inform me of any problems. Still those drivers did not work before I edited that modules.dep. Nevertheless, it shouldn't do any harm if one checks modules.dep just to make sure that Ubuntu loads correct fglrx.ko at startup, should it?

---

### Post by mlomker on 2005-10-01
No, it's just easier to use the depmod command or delete the old .ko file prior to the install.  ;)

---

