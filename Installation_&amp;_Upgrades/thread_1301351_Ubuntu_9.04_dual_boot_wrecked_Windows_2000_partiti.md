---
title: "Ubuntu 9.04 dual boot wrecked Windows 2000 partition"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by n6vig on 2009-10-25
Hi all.

I took an old PC out of storage and put a fresh install of W2K on an NTFS partition. Then I installed Ubuntu 9.04  with all the defualt settings for dual boot. Now Ubuntu works, but W2K makes it to the "Starting up..." screen, then fails with an "INACCESIBLE_BOOT_DEVICE" blue screen. When I run CHKDSK, it says my NTFS partition has unrecoverable errors.

What did I do wrong, and what should I do different when I re-install?

Thanks.

---

### Post by Dark_Stang on 2009-10-25
Probably a bad hard drive if it has never been replaced before, or the filesystem may have been corrupted.

---

### Post by Bartender on 2009-10-26
Yeah, it's Ubuntu's fault that you drug some dust-filled old PC with a dead CMOS battery out of the closet and expected everything to work.

Open the old POS up, blow the dust out, replace the CMOS battery.  Replace the dessicated thermal paste on the CPU and the North/South Bridges if applicable.  Use GParted LiveCD to wipe the drive clean, then create a primary NTFS partition for Windows out of one half the drive and install it to just that partition, not the entire drive.  Run scandisk and memtest.  If the HDD doesn't show a bunch of bad blocks and RAM still works, then reinstall Ubuntu to the rest of the HDD.

Did you even check the Ubuntu disc for errors?

---

