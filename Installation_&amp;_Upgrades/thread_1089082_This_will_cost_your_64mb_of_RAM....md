---
title: "This will cost your 64mb of RAM..."
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by IxAxU on 2009-03-06
Hi, I'm trying to install Kubuntu. 
I get these errors;
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave aperture memory hole
[    0.004000] Please enable IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM

Then the busybox v1.10.2 prompt loads.. and I'm able to type commands in..

So my problem is kubuntu needs 64MB of ram..
How would i enable IOMMU where would I look for that?
... 

Thanks!

---

### Post by ilioscio on 2009-03-06
Scratch my last post, don't think it's related. Still looking around.

---

### Post by IxAxU on 2009-03-06
> **ilioscio said:**
> Scratch my last post, don't think it's related. Still looking around.

[0.004000]Aperture beyond 4GB. Ignoring
[0.004000]Your BIOS doesn't leave a aperture memory hole.
[0.004000]Please enable the IOMMU option in the BIOS setup.
[0.004000]This costs you 64MB of RAM.

Same problem pretty much, except it's not the beyond 4GB..
[0.004000]Your BIOS doesn't leave a aperture memory hole.
[0.004000]Please enable the IOMMU option in the BIOS setup.
[0.004000]This costs you 64MB of RAM.

how would i go about enabling IOMMU .. I don't have any settings like that.. 

I have memory hole remapping enabled.. not sure if that is what i need to disable.. I won't disable it until I'm told too.

---

### Post by ilioscio on 2009-03-06
[[COLOR="Navy"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1018854") thread seems to go over your issue, if i'm not mistaken this time. :-P

---

### Post by 1BigBore on 2009-03-28
> **IxAxU said:**
> Hi, I'm trying to install Kubuntu. 
I get these errors;
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave aperture memory hole
[    0.004000] Please enable IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
<<snip>>

Thanks!

I am getting that EXACT Message except I get a :
[0.560497] Kernel Panic - Not syncing : VFS : unable to mount Root FS on unknwn block (0,0)
as a last line, and I get nowhere after that... I cannot edit my "/boot/grub/menu.lst"  so I am going to try and reinstall and then boot from disk to do the editing.  

Does this sound right...

Thanks for any hints.
Oh yes, my "new" computer is an AMD dualcore 2.5 gig on an ASUS motherboard with 4 GB ram and a GeForce 8400 video card.

p.s.  After 3 installs, I let the program resize the partitions and it will now boot well enough to use the computer.  I still get the lost memory message, but at least it works.

---

