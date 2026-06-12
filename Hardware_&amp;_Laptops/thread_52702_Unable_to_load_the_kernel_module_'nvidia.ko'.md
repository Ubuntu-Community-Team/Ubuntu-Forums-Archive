---
title: "Unable to load the kernel module 'nvidia.ko'"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by tseliot on 2005-07-28
Hi, I've never managed to install any Nvidia driver in Ubuntu. In PclinuxOS it can be easily installed by using the nvidia installer (v.7667). This doesn't work in Ubuntu as it can't compile the modules for my kernel (2.6.12-k8dma compiled from Breezy sources). The only kernels I can use are 2.6.12.x series.

This is the log

[http://tseliot.95mb.com/nvidia-installer.log](http://tseliot.95mb.com/nvidia-installer.log) 

I hope somebody can help me

---

### Post by Juergen on 2005-07-28
Why don't you just install the modules via apt/synaptic?

Not the newest, but at least they work (for most people, at least ;-)).

There is 'nvidia-glx', and maybe 'linux-restricted-modules'.
I don't know if you need the latter, but there's 'nvidia' in it's description.
If you don't want to fiddle around in your config:
> To enable the driver, run "sudo nvidia-glx-config enable"
You have to activate the 'restricted' repository for this (maybe others) but you'll probably have done that anyway.

---

### Post by Juergen on 2005-07-28
Well, I wrote a long reply how to install them via synaptic, and then deleted it after I realized that you backport your kernel ;-)

Are you sure you have the right linux-headers installed? If they are for the original Hoary kernel that might conflict.

Look in synaptic if you have linux-headers that don't match.
Since you have the source installed, you wouldn't need such a package at all (IMHO)

---

### Post by tseliot on 2005-07-28
I can't see any kernel image or header called "2.6.12-k8dma" in Synaptic. It's strange because their folders are in /usr/src and if I prompt "uname -r" it gives me "2.6.12-k8dma".

---

### Post by tseliot on 2005-07-29
I've also tried Tamir's kernel but I can't get Nvidia drivers to work. On the other hand he can. So there must be something else which I need to do. My card has 256mb RAM and I'm using as a vesa because "nv" is buggy and the screen gets really messed up after a while (expecially in KDE).

Any ideas?

---

### Post by tseliot on 2005-07-29
Wait, I can see my kernel and headers in synaptic (I looked for linux image instead of kernel image before).

I've noticed the installer works with kernel 2.6.11. I can't use this kernel as it doesn't support the "no_timer_check" function so the system clock works at double speed.

Doesn't nvidia driver work with kernel 2.6.12???

---

### Post by Tamir on 2005-07-29
[QUOTE=tseliot]Wait, I can see my kernel and headers in synaptic (I looked for linux image instead of kernel image before).

I've noticed the installer works with kernel 2.6.11. I can't use this kernel as it doesn't support the "no_timer_check" function so the system clock works at double speed.

Doesn't nvidia driver work with kernel 2.6.12???[/QUOTE]
 Ofcource it is. I am using it. :) you should have the kernel-headers with same version.

---

### Post by tseliot on 2005-07-29
Yes, I have them. Perhaps could the cause be the new VESA support I enabled in my kernel?


However I compiled a new kernel from a vanilla one. The nvidia installer compiles the modules but the problem comes when it asks me if I want to install OpenGL 32bit compatibility libraries. Here's part of the log:

   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32bit compatibility OpenGL libraries? (Answer: Yes)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> done.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (1.0-7667):
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86_64 (1.0-7667) is complete.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (1.0-7667):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
       (expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
       '/usr/lib32/libGL.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by tseliot on 2005-07-29
There's an error when I accept to install ia32 OpenGL compatibility libraries (I have an AMD64)

ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
(expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
'/usr/lib32/libGL.so.1'). The most likely reason for this is that
conflicting OpenGL libraries are installed in a location not inspected
by `nvidia-installer`. Please be sure you have uninstalled any
third-party OpenGL and third-party graphics driver packages.

How could this be solved?

---

### Post by Juergen on 2005-07-29
>  '/usr/lib32/libGL.so.1'). The most likely reason for this is that
conflicting OpenGL libraries are installed in a location not inspected
by `nvidia-installer`.
Do you have 'xlibmesa-gl' installed? That package installes this file.
If so, remove it.

---

### Post by tseliot on 2005-07-29
I have xlibmesa-gl, xlibmesa-dev, xlibmesa-glu,  xlibmesa-glu-dev. Shall I remove them all?

---

### Post by tseliot on 2005-07-29
If I remove xlibmesa-gl it will remove many things: gdm and many other important programs among them.

What should I do?

---

### Post by tseliot on 2005-07-29
SOLVED!

At last I managed to install nvidia drivers 7667 with nvidia installer. I haven't installed openGL 32bit but now I can use the kernel I compiled from Breezy source (which I use in Hoary) .

I've found the solution in this thread

[http://www.ubuntuforums.org/showthread.php?t=39675&page=2&pp=10&highlight=xlibmesa](http://www.ubuntuforums.org/showthread.php?t=39675&page=2&pp=10&highlight=xlibmesa) 


UPDATE: I've written this HOWTO

[http://www.ubuntuforums.org/showthread.php?p=277659#post277659](http://www.ubuntuforums.org/showthread.php?p=277659#post277659)

---

