---
title: "Dual booting on two different drives"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by travnasty on 2008-12-30
I just want to make sure that I can do this, and it won't cause any problems.

Ok, so I have a 80 GB IDE hard drive and it is set up as slave to the master CD/DVD/Burner (this is the only possible way to set it up due to the cable). I have a 1000 GB SATA drive which has XP installed on it. Now, I want to install Ubuntu 8.04 on my 80 GB IDE drive, and have it dual boot with my XP on the terabyte drive.

A. Is there anything outside of the installation that I would need to do to set this up?

B. If I removed the 80 Gig IDE drive, would I be unable to boot into windows?

C. Do you have any further advice for this set up?

Thanks, and I appreciate your help.

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Shouldn't hurt anything. I've heard of people accidentally install grub on the wrong drive and that causes some problems with booting winblows but don't know how they managed that. Anyway... all you'd have to do is specify the right drive during the installation in gparted (the partition editor) and install. You might have to hit esc to enter the bootloader and chose the drive you want to boot depending on which OS you want to use but that only takes a sec. You might want to research that "grub on the wrong drive" thing because it might install on the master drive by default. I've had no problems dual booting on one hdd.... (except that I used Vista and that OS is crap)

---

### Post by Pumalite on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

