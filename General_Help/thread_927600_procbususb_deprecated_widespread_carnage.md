---
title: "/proc/bus/usb deprecated? widespread carnage?"
date: 2008-09-23
forum: General Help
---

### Post by pbhj on 2008-09-23
It appears that having usb devices under /proc is deprecated and so none of my usb stuff works including lsusb. It could well be that I've just noticed this and that a workaround was simply wiped out by my updating.

I've stupidly been caught in a frenzy of upgrading and have upgraded to Ubuntu + KDE with Intrepid "alpha-6" (alpha for 8.10). I can now boot to the older kernel 2.6.24 I had and connect to the 'net or boot to the new kernel 2.6.27 and have X working (under the nvidia-glx-177 drivers).

Anyway, am I mistaken? Has the mounting of usbfs under /proc/bus/usb been removed from Ubuntu for a while?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483392](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483392)
[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/comments/5](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/156085/comments/5)

The second of the above refers to this happening in July 07, has it just worked it's way out into Intrepid or have I done something else that prevents lsusb, my usb printer and my usb modem from working? Note that kde's system information applet gives the correct usb tree.

Any help gladly received.

---

