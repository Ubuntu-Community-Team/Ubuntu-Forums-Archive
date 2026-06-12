---
title: "Wubi with bitlocker"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by wongjos1 on 2009-04-20
I believe I might have a workaround using Wubi and Bitlocker.

What I did was made two custom partitions on Windows. I kept a large main partition, C, and a smaller 20GB partition, S.

I activate Bitlocker and it encrypts my C drive. The other partition, S, remains un-encrypted because Bitlocker needs to place the decryption routine there. 

Then I used Wubi to install Ubuntu onto the S drive. The installation went through without any problems. 

The first time I rebooted, GRUB complains about not being able it's files. However, once I copied the files wbuildr and wbuildr.mbr found in C:\ to the S drive, GRUB is able to load and run Ubuntu. 

There's still a bunch of error messages that come up, but they don't seem to interfere with Ubuntu or GRUB. I'm guessing the bootloader tries to access the C drive first and when it can't find the files, it'll check all other drives.

---

### Post by DouglasAWh on 2010-01-20
this should work for Vista, but Win7 does not give that drive.  Does anyone have a work around for Win7?

---

### Post by DouglasAWh on 2010-07-14
Any news on this?  I'd really like to begin using Wubi with full disk encryption, but it doesn't look possible.

---

