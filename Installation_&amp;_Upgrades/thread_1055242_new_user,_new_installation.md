---
title: "new user, new installation"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by meebers on 2009-01-30
How do I change a "live" installation into a permanent install on the HDD.  There has to be an option somewhere isn't there?? :( Tx

---

### Post by jeffjanzen on 2009-01-30
"live" means you're running Ubuntu from an install CD. it's actually not installed, even though it may seem an awful lot like it is.  but there should be an "install" icon on the desktop that you can double-click to begin the permanent installation on your HDD.

---

### Post by meebers on 2009-01-30
> **jeffjanzen said:**
> "live" means you're running Ubuntu from an install CD. it's actually not installed, even though it may seem an awful lot like it is.  but there should be an "install" icon on the desktop that you can double-click to begin the permanent installation on your HDD.

There is, I double-clicked it, ubuntu went off and did something for about 15 seconds and then returned to the desktop.  That was ver 7.10, I am now in the process of D/L 8.04 (74%) and will try with that.  I did try to upgrade to 8.04 on the update manager and it said I did not have enough HDD space.?  (using a spare 30 GB)

---

### Post by avtolle on 2009-01-30
Is the spare 30GB space in an existing partition, or is it just unallocated on the disk? If it is within an existing partition, you will need to shrink that partition to make it available. BTW, if you have another OS on the computer right now, such as XP or Vista, defrag the drive (more than once) before trying to shrink the existing partition to free up the space (if, indeed, the spare space is within such partition); and if Vista, use the Vista tool to shrink the Vista partition.

---

### Post by Rompalle on 2009-01-30
> **meebers said:**
> There is, I double-clicked it, ubuntu went off and did something for about 15 seconds and then returned to the desktop.  That was ver 7.10, I am now in the process of D/L 8.04 (74%) and will try with that.  I did try to upgrade to 8.04 on the update manager and it said I did not have enough HDD space.?  (using a spare 30 GB)

You should download the latest version of 8.10. Put your spare disk in and boot the cd, choose your language then "Install Ubuntu".

---

### Post by meebers on 2009-01-30
> **avtolle said:**
> Is the spare 30GB space in an existing partition, or is it just unallocated on the disk? If it is within an existing partition, you will need to shrink that partition to make it available. BTW, if you have another OS on the computer right now, such as XP or Vista, defrag the drive (more than once) before trying to shrink the existing partition to free up the space (if, indeed, the spare space is within such partition); and if Vista, use the Vista tool to shrink the Vista partition.

What I did to be safe, was to configure the computer with only 1 HDD, which was just formatted before the install began.  No other OS installed.  I like to use removable HDD enclosures, and only turn on the power (key) with the OS (HDD)I want.  Right now, Ubuntu is the only player. :)  (looks like my download has finished, be back in a while) Tx for the comments

---

### Post by meebers on 2009-01-30
> **Rompalle said:**
> You should download the latest version of 8.10. Put your spare disk in and boot the cd, choose your language then "Install Ubuntu".

I am going to try 8.04 LTS 64 bit version, because that what was offered under the update manager while "live" with 7.10.  If it does not install, will try the normal 8.10 version.  Tx

---

### Post by jeffjanzen on 2009-01-30
although that makes the install "safer", it will prevent the grub-installer from detecting windows and adding it to the boot menu. just be prepared to go into /boot/grub/menu.lst once you've booted into ubuntu successfully and add windows to the menu.  details are probably available in the ubuntu documentation: help.ubuntu.com.

---

### Post by meebers on 2009-01-30
The D/L and burn to dvd was fine, install went fine, this time a nice interactive menu was presented for the install on the HDD.  Everything was ok until the first boot from the HDD when an error message came up "GRUB Loading STAGE 1.5 Read Error". :( Tried several re-boots with same error, tried another complete re-install with the same error message.  So.....now d/l ver 8.10.  The 8.04 ver that I d/l was the 64 bit version, perhaps unique to that.??  My system is AMD x64, dual core, 2g ram, abit MB.  TIA

---

