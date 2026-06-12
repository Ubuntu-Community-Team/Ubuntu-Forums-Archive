---
title: "thinkpad x20 undocking problem"
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by droebbel on 2005-01-24
I've finally done it: Hot docking/undocking into the ultrabase basically works. But if I suspend with the computer being undocked, I get the following error on resuming:```
hdc: bus not ready on wakeup
hdc: drive not ready on wakeup
...
``` As soon as I dock, resuming continues. Of course, there is no /dev/hdc device at all at this time, as I had unloaded the ide-cd and cdrom modules before undocking.

This is what I have already done before undocking:

unmount drives
remove icd-cd, cdrom, lp, parport-pc, parport, floppy modules
switch dma off on hdc (got errors sometimes after redocking, switch it on again later...)
echo eject > /proc/acpi/ibm/bay

after which the light on the ultrabase goes out, and I can undock without it beeping (sounds good, I thought...).

But no... 
Although I had unloaded the cdrom the modules, the kernel still wants to acces the hdc drive which had once been there.
It seems the ide bus has to be unregistered too, right?
There is some "ultrabayd"-script, which should do something like that, but obviously doesn't for me. Anyway: If I run hdparm -U 1 /dev/hdc before undocking, it does not help. Output is then ```
/dev/hdc:
 attempting to unregister hwif#1
``` No Idea if it really *did* unregister it. The error on resuming (undocked) remains the same.

Some more information:
In /proc/ioports I find the line 1808-180f : ide1, which remains always the same (docked/undocked/unregistered?).
Kernel is 2.6.8.1, the rest of the system is hoary. special ibm-api stuff is installed.

How can I tell the kernel to forget about that stupid drive?

[I always booted docked. Else I could net get any of the ultrabay devices recognized at all.]

---

### Post by droebbel on 2005-01-24
Ok then, I found it.
I managed to unregister the drive with hdparm finally, though I could not get it back...
idectl from the original hdparm source did not work for me, but hotswap does.
apt-get install hotswap, and use the following commands:

hotswap -c 1 unregister-ide (before undocking)
hotswap -c 1 rescan-ide (after docking)

That's all.

---

### Post by rushibhai on 2005-12-01
Are you able to use DMA after reinserting the CD drive? I get
/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

if I try to turn on DMA.
Ubuntu breezy.

---

