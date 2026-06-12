---
title: "Something odd at start-up"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by mrpinchy on 2009-10-21
Hey All,

I don't believe this is a problem but it seems odd none the less.  Noob here by the way.

I have a dual boot set-up.  9.04 32 bit & Vista 32 bit, running on a Compaq laptop. 
AMD Athlon X2 64 
Atheros sound
NVIDIA graphics
can't remember the rest.

Anyway, when I start my box up it gives me the boot screen where I can choose what OS I want it to boot with.  I have four choices of Linux kernels on that screen.  They end with 12, 13, 14 and 15.  Should I go into synaptic and remove the previous versions, or is it normal to have them all there at start-up.

I have been running Ubuntu for about five months with very few issues, so I couldn't be happier.

Thanks,
Joe

---

### Post by gareththegeek on 2009-10-21
AFAIK its normal to have them there, they are all the previous kernel version you have had installed. Presumably the newer kernels have been install as you have run updates.

You could uninstall the older kernels or just remove them from the grub screen, but if it ain't broke...

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

```
sudo gedit /boot/grub/menu.lst
```
use # to comment out old grub entries.

---

