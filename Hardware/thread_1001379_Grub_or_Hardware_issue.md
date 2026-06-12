---
title: "Grub or Hardware issue?"
date: 2008-12-03
forum: Hardware
---

### Post by d4ng3r on 2008-12-03
Alright so I'm not sure if the hardware on my HP dv5220us laptop is broken or if its Grub, here is a rundown of what happened.

A week or so ago My computer stopped booting, I would power it on and it would hang on the HP screen and never go into GRUB (I have a dual boot with Win XP).  BIOS was incredibly sluggish and even booting from CD took ages if it worked at all, so I sent it into HP for repair.  They sent it back to me with description "Cleaned UVA/CPU fan and resealed Hard drive"  When I turned it on it worked fine.  That was Monday afternoon.

Sometime Monday I installed a large group of updates and restarted and it was fine.  After the restart I installed a few more updates, one of them failed (because I stupidly made the mistake of putting /boot on a small, independent partition, which ran out of space before one of the Kernel updates could complete.  I meant to fix it, but got busy and forgot about it, and when I restarted my computer this afternoon it hangs yet again at the HP screen like it did before.  Now this time its slightly different:  Last time the Ubuntu 8.1 CD I borrowed from a friend would not run from startup (it would give an error and crash... I am running 8.04 LTS btw)  This time though, that same CD does run, but does not find my computers Hard drives (any of the partitions) at all so I'm not sure if My hard drive/motherboard is fried, or if I just messed up Grub, and 8.10 is just also coincidentally not working correctly.

Any ideas/ help would be greatly appreciated
-Brian

---

### Post by cariboo on 2008-12-03
I would suggest going to the hard drives manufacturers web site and download their diagnostic tools and run them, just to check what shape your hard rive is in. You may also want to pull the cover from the hard drive pocket and make sure that it is connected properly as it may have come loose during shipping.

Jim

---

### Post by pytheas22 on 2008-12-04
I would try following the advice above for checking the hard disks.  You should also make sure that SMART is enabled in your BIOS, and see if BIOS has the ability to do any other hardware checks.

To me it sounds like your hard disk (or possibly merely the cable or connector) is fried, but nothing's certain.  I would try booting to a few different live CDs; if they all work without a problem yet fail to detect your hard drive, the disk is probably broken.

Also, if the live CD can detect any hard disk at all (i.e. if an entry for 'hda' or 'sda' exists anywhere in your /dev directory), try mounting it (or a partition on it)...it could be merely that the partition table or something is corrupted, which is a software, not hardware, problem.  If the mount command complains about a dirty file system, I would check out the partition structure.

---

### Post by d4ng3r on 2008-12-13
So I went to the BIOS Hard disk Diagnostic test (after waiting the 800 years for BIOS to load), and it says no IDE device detected.  Unbuntu disk doesn't find any /hda or /sda partitions to mount.  And I reopened the hard disk enclosure and everything looked good and tight.  Any way for me to check the partition table before I ship it off with my fingers crossed?

Thanks
-Brian

---

### Post by pytheas22 on 2008-12-14
> Any way for me to check the partition table before I ship it off with my fingers crossed?

If Ubuntu can't detect the existence of any devices at all, then unfortunately no, I don't think there's any way for you to check the partition structure.

If BIOS takes a long time to load, it does sound like hardware failure...it's probably taking a long time to detect the hard disk (does it still take 800 years if you unplug the disk before turning on the machine?).

---

