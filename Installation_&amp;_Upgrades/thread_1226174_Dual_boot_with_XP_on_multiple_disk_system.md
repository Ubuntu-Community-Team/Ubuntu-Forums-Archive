---
title: "Dual boot with XP on multiple disk system"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by MikePerryUK on 2009-07-29
I want to install Ubunto 9.04 on a PC with XP Pro already installed.  The PC has 3 disks, all formatted NTFS currently.  C: drive has XP, D: drive is for data, the other drive is partitioned as E: and F:, both empty.

I want to put Jaunty in what is currently F: drive and have boot options that allow me choose which OS to boot into, with XP as the default.

Last time I tried, it put Grub into the MBR of C: drive!  I think I must have been confused by the different drive naming as it asked where it should be put - I must have made a wrong choice, but what is the correct one?

Any suggestions please? 

Thanks :)

---

### Post by lavezarez on 2009-07-29
hi mike,

some links that might help you out, in case you haven't seen them yet:
1. ubuntu forum post - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
2. another [link]("http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/") - uses dapper, not jaunty but the installation is similar

---

### Post by MikePerryUK on 2009-07-29
Thanks, lavezarez

I think the second link showed me how to identify my disks and what they are named in Linux.  Last I tried showed them as sda, sdb, sdc1 and sdc2.  
It also asked where to put Grub, where should that go (assuming Jaunty is installed on sdc2)?
Thanks:D

---

### Post by Mark Phelps on 2009-07-30
Couple of suggestions ...

First, I believe that Ubuntu will default to writing the MBR code to the "first" hard drive it finds, which in your case, should be the C:\ drive.  You also have the option of writing that to the same drive that Ubuntu is installed on.

Which brings me to my second suggestion: consider booting from the Ubuntu drive, overwriting its MBR, and adding an entry to menu.lst for XP.

---

