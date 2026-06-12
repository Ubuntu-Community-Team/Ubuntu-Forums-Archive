---
title: "LiveCD running of HDD"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by audrich on 2009-08-29
I am trying to install Ubuntu on a laptop that has no optical or floppy drives and unbootable USB drives.  My solution is placing the 9.04 LiveCD on a slim partition of the HDD and booting from there.  I did that, broke it down into:

hd0,0 ex4 intended location for installed OS
hd0,1 swap
hd0,2 ex3 LiveCD+SuperGrub

I successfully boot the LiveCD from hd0,2 and run the installer.  In the installer menu, I naturally choose hd0,0 as the location for "/".  

At this point it stops me.  It's telling me it can't go through with the installation until I unmount /cdrom.  Considering the computer has no physical CD-ROM, and /cdrom is busy when attempting to unmount, somehow it is mistaking hd0,2 (LiveCD) as /cdrom, which interferes with designating hd0,0 as / somehow.

Can someone tell me how to resolve this?  I imagine it involves editting something that tells LiveCD it is NOT at /cdrom.  Help would be greatly appreciated with this.


And without going into more detail, no I cannot do a simple install via removable media or network so don't bother suggesting that; booting from HDD is my only option for this relic machine, trust me.

---

