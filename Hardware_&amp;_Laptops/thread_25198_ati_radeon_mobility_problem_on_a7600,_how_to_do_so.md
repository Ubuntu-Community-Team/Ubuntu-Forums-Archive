---
title: "ati radeon mobility problem on a7600, how to do some dsdt-fixing?"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by Muffen on 2005-04-09
Hi!

I have a problem after upgrading to xorg on my fujitsu siemens A7600 laptop. I'm running kubuntu and the newest ubuntu kernel. When I was running xfree86 everything worked reasonably well, only problems was that I had no 3d support for my 3dcard (ati radeon 320m igp, only 2d support), and some trouble with the usb. But now, when I upgraded to xorg, the computer freezes when I try to start the xserver with the ati-driver (the ati-driver worked well on xfree86). So I have to use either the vesa driver, or go back to xfree86.

But I found this site: [http://groups.yahoo.com/group/amilo/message/530](http://groups.yahoo.com/group/amilo/message/530) which seems to address my problems. It seems there is possible to get the ati-driver working again and maybe even fix the usb-problems by making my own DSDT-table. But it says I have to compile my own kernel, how do I do that? Can I get the source for the ubuntu-kernel somewhere? Would I have to recompile every single time the ubuntu-kernel gets updated? Is there an easy way to "make my own DSDT-table" in ubuntu? Anyone have any tips?

---

### Post by alastair on 2005-04-09
I would think twice before doing something like "make my own DSDT-table". I looked at the link and it is all for kernel 2.4 as well. Unless you are really desperate or brave, why not :

a) use the "radeon" driver
b) wait for a kernel upgrade and/or a newer ATI driver

---

### Post by Muffen on 2005-04-10
Thanks for the reply.

Ok, if there is no easy way to do it, I guess I wont try, as I'm a linux newbie and don't want to ruin my system :)

But it could be nice to do it anyway (if I could get it to work with ubuntu), as it could fix my usb problems too, but maybe everything will be fixed in a later kernel.

But how do I use the radeon driver in xorg? On the list over drivers I get when going to dpkg-reconfigure xserver-xorg there is no "radeon" driver. And when I pick auto-detect it says I should use the ati driver, but as I said in the above post, that doesn't work because of the dsdt/irq problems.

Well... I'll just sit around waiting for the next kernel then... sigh.

Oh, now I noticed that my sound has gone too. Back to xfree86 for me.

---

### Post by maqi on 2005-04-10
Have a look at [this](http://ubuntuforums.org/showthread.php?t=24557) thread. 

Hopefully this will help you out.

cheers,
maqi

---

### Post by gree on 2005-09-11
here [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)
good guide, on how to fix your dsdt file.

either build it into the kernel, load as initrd, or merge it with an existing initrd, which i did NOT get to work with ubuntu 5.10.

i made this work in Gentoo, and some while ago in Hoary too,
it will fix the black screen, and let you use the outer usb ports, and should fix the touchpad too (i had problems with that, have to insert a ps2mouse to get it working, can unplug after)

here you can find custom dsdt files for the 7600.
dont think i can send you my own file.

[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

[http://koti.mbnet.fi/~keiky/misc/linux/amilo/amilo_linux.html](http://koti.mbnet.fi/~keiky/misc/linux/amilo/amilo_linux.html)
this guy have good info for our buggy laptop.

--
made gentoo work great on my 7600, but takes so darn long time to emerge what i need, but i cannot get the dsdt to work in ubuntu again.
last time i did "something".

---

### Post by mlomker on 2005-09-11
Have you tried some of the drivers available out there?  My last laptop had the same card.

[Look here.](http://rzr.online.fr/docs/comp/gfxcard.htm)

---

