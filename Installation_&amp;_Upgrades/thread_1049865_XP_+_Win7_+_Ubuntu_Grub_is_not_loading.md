---
title: "XP + Win7 + Ubuntu: Grub is not loading"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by Amadaeus on 2009-01-25
Hey guys... I'm a little stuck here and the Interwebs is so far of no help...

My system has two hard drives: sda1 is primary used as storage (an old drive...) and sda2 is the drive with the OS'es. System already has XP. I used GParted to partition the disk into 4 chunks: A 250Gb chunk for XP, a 150Gb chunk for Win7, a 70Gb chunk for Ubuntu and a 10Gb chunk for swap.

After partitioning, I install Win7, and all goes well. The Win7 bootloader shows up and I can access both XP and Win7 from the new bootloader.

I then install 8.10. Mount "/" into the 3rd partition and designated the fourth partition as the swap partition. The install goes smoothly, disc gets ejected, and the system reboots... but when the system reboots I'm not seeing the reassuring glow of GRUB, instead the Win7 bootloader is present and of course Ubuntu is not a boot option.

I've followed instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to try to get Grub loading, but it's not working.

Does anyone have any ideas?

Thanks,

-A

---

### Post by Amadaeus on 2009-01-25
Never mind guys, I figured it out.

It's because my OSes are sitting pretty on hd1, the grub bootloader was pointing to hd0, so in effect I it was working... just not working at the right place.

The key command in grub I ran was "setup (hd1)" rather than "setup (hd0)". After that, Grub works like a champ.

---

