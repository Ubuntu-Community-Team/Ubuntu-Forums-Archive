---
title: "installing XP over Vista, in a dual-boot"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by kedmond on 2009-03-06
Hey all,
    I have a Dell Latitude E6400.  It came with a 32bit version of Vista Business installed.  I managed to split the disk and install Ubuntu 8.10 on the 2nd half of the disk.  Grub works great.  After having gotten tired of Vista, I want to install XP over it.

    I plan on formatting the Vista partition and installing XP SP3 over it, along w/ all of the appropriate Dell drivers.  Will this screw up Grub and then mess up the accessibility of my Linux partition?  I'd appreciate the help, thanks.

-Kazem

---

### Post by Mark Phelps on 2009-03-07
Yes it will .. in true MS fashion, it ignores what else you have on the drive and overwrites the MBR to wipe out GRUB.  You will need to reinstall FRUB from the live CD after that.  See the following link:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kedmond on 2009-03-08
Yeah, I figured it out, thanks!

---

