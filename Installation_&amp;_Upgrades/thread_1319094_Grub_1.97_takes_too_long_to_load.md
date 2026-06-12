---
title: "Grub 1.97 takes too long to load"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Noiano on 2009-11-08
Hello everyone,
I have installed Ubuntu 9.10 (clean install) and I have notice an unusual delay when loading grub.
With previous version there was allmost no delay from the moment in which "loading grub" was displayed and the appearence of the menu with all the bootable entries.
Now ten seconds pass from the "loading grub" notification to the grub menu.

**Why** I wonder...it's just me?

Thanks

---

### Post by b.bhargav on 2009-11-26
> **Noiano said:**
> Hello everyone,
I have installed Ubuntu 9.10 (clean install) and I have notice an unusual delay when loading grub.
With previous version there was allmost no delay from the moment in which "loading grub" was displayed and the appearence of the menu with all the bootable entries.
Now ten seconds pass from the "loading grub" notification to the grub menu.

**Why** I wonder...it's just me?

Thanks

Even I'm having similar problem after upgrading to GRUB 1.97

---

### Post by JackCorbae on 2009-12-25
10 Seconds? Mine takes over a minute - fresh install of Ubuntu 9.10 64bit and the only thing that I can think of is that it has something to do with the fact I have a mirrored SATA boot disk and a single smaller SATA disk which is where Ubuntu wanted to put Grub but the BIOS has the mirrored drive as the boot disk.

When I moved grub onto the mirrored drive, after much messing about, it worked but is unbelievably slow.

---

### Post by oldfred on 2009-12-26
Do you have multiple drives and many partitions with operating systems? Grub needs to be on the same drive as the ubuntu install. It sped up my boot by about 20 seconds. I have 3 drives, 4 systems and many partitions.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

### Post by AlexMinsk on 2010-05-29
> **oldfred said:**
> Do you have multiple drives and many partitions with operating systems? Grub needs to be on the same drive as the ubuntu install. It sped up my boot by about 20 seconds. I have 3 drives, 4 systems and many partitions.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

Can you please explain in details?
I've tried the command, but it didn't help

---

### Post by wilee-nilee on 2010-05-29
> **AlexMinsk said:**
> Can you please explain in details?
I've tried the command, but it didn't help

If you really need help start a new thread. ;) This one is 6 months old, and you need to explain the OS your running and what your problems are, this slow boot from grub-pc is not happening now,  but this doesn't mean that you may have problems.

---

