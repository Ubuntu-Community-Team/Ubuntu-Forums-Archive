---
title: "Remove GRUB on notebook"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Flatron on 2007-10-22
I know that there are many topics about that, but my problem is a bit different.

I have a Lenovo laptop, and it has a pre-installed partition on the disk, which contains the OS installer and some rescue & recovery tools. Normally, if I press the Lenovo Care button (special button on the notebook) when the bios is loading, it loads the rescue & recovery system.

The problem is that after the kubuntu install, this button doesn't work well, if I press it, the system asks me to choose a boot device (hard drive, cd, network...), and because of the need of space, I should remove the kubuntu.

I read the posts about the fixmbr solution, but how could I fix the pre-installed partition boot?

---

### Post by GrammatonCleric on 2007-10-22
Have you tried the Bios Button + F1 at the same time?  I've read somewhere that's the key combo to get into the bios post Ubuntu.   Are you sure that the recovery partition is still there?

-GC

---

### Post by Flatron on 2007-10-22
Yes, that's still there, the grub created a boot entry for that. The F1 is the button to go to the bios menu.
I wrote wrong in my first post, if I press the lenovo care button, I can choose load bios menu, make normal boot and select boot device, so the bios cannot find the partition, and gives me this.

So if I remove the grub, I won't be able to reach that partition.
I tried to make that partition active, but the grub came again.

---

### Post by staticsage on 2007-10-22
What exactly are you trying to do? Are you trying to access the rescue and recovery partition?

If you select to boot the rescue and recovery partition from grub, what happens?

---

### Post by Flatron on 2007-10-22
It loads well, the question is how to load it when I remove grub?

Fixmbr fixes only the installed OS's boot partition, doesn't it?

---

### Post by staticsage on 2007-10-22
How was it loaded before you had grub? Did you select it from the Windows boot manager (NTLDR)? If that is the case, do you still have your windows install on the disk?

Basically my idea is that if it was being loaded from the NTLDR, then I think we can recover the functionality if you still have your windows install in tact.

---

### Post by Linicks on 2007-10-22
I think what has happened here is the kbuntu install wiped the utilities partition.

Flatron, post the output of:

> sudo fdisk -l

(that is a lower case -L )

in here.

Nick

---

### Post by Flatron on 2007-10-22
staticsage:
Before grub install, Windows made a normal boot. The rescure partition only booted when I pressed the Lenovo care button under the bios loading. That partition is still there, I'm sure.

Linicks:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         622     4989952   27  Unknown (Pre-installed stuff)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         623        4538    31455270    7  HPFS/NTFS  (Windows XP)
/dev/sda3            4539        7149    20972857+  83  Linux (Kubuntu)
/dev/sda4            7150       14593    59793930    f  W95 Ext'd (LBA)
/dev/sda5            7150       14332    57697416    7  HPFS/NTFS (Storage)
/dev/sda6           14333       14593     2096451   82  Linux swap / Solaris (Swap)
```

If i set the pre-installed stuff's partition active, it still loads the grub.

---

### Post by staticsage on 2007-10-22
> **Flatron said:**
> staticsage:
Before grub install, Windows made a normal boot. The rescure partition only booted when I pressed the Lenovo care button under the bios loading. That partition is still there, I'm sure.

I'm just trying to figure out how exactly it gets into the partition when you press the button. I'm trying to figure out where that functionality is built in. Typically those buttons are controlled by the BIOS (like the ones that control your wireless card: for me it's Fn+2 on my Dell). If that button is controlled by BIOS, it shouldn't be affected by the boot loader at all.

Since it worked with the original boot loader, but not with grub, it seems that it's not the BIOS... before I go on I"m going to research the ThinkVantage button that you have. I'll post back shortly.

---

### Post by staticsage on 2007-10-22
Got it. It uses its own bootloader:

[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

From windows command prompt:
```
cd C:\Program Files\IBM ThinkVantage\Common\BMGR
bmgr32 /Fbootmgr.bin /v
```

Next time you install Ubuntu, you have to install Grub to a separate location. This is the first tutorial I came across: [http://physicsmajor.wordpress.com/2007/03/03/my-ubuntu-installation-on-thinkpad-r60-dual-boot-with-winxp/](http://physicsmajor.wordpress.com/2007/03/03/my-ubuntu-installation-on-thinkpad-r60-dual-boot-with-winxp/)

I'm sure there are better ones out there. It is the exact same thing as trying to keep NTLDR in place.

Post back with your results! :)

---

### Post by Flatron on 2007-10-22
Intresting page, I boot the win and try that.

---

### Post by Flatron on 2007-10-23
Sorry for the late post, I had a little problem.

That method didn't solved the problem, but after a fixmbr, fixboot in windows XP recovery mode, and then the thinkvantage bootmanager-fix solved it.

Probably the GRUB overwrittem the MBR to skip the sensing of active partition, and maybe it removed the sectors written by the service partition's boot manager.

The bmgr fix searched free sectors in the beginning of the disc, so the bios probably searches for some boot data after the MBR, and try to load the service partition from there.

Thanks for your help.

---

