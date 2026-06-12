---
title: "Ati Mobility Radeon 9600 error, x won't start"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by Didius on 2005-09-16
Hi,

I had some troubles with my notebook's graphics. (ATI MOBILITY RADEON 9600)
I followed the Radeon How to.
But then my X didn't want to start.

The How to requested these outputs;

@Portable:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

@Portable:~$ dmesg | grep fglrx
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0

@Portable:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "keyboard"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "ati"


Can somebody help?

btw; before i followed the how to, i installed the "ATI Driver Installer" from their website (perhaps that has something to do with it?)

---

