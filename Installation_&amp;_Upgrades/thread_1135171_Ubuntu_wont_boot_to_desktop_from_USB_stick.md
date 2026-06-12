---
title: "Ubuntu wont boot to desktop from USB stick"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by jonathan777 on 2009-04-24
Hello, i've just installed Ubuntu 9.04 from a live CD to a 4GB flash drive and it doesn't boot into the desktop, I just get presented with "boot:" command prompt. Anyone help?

Thanks.

---

### Post by jonathan777 on 2009-04-25
Nevermind, i've sorted it (Had to reformat the flash drive to FAT - It didn't seem to like FAT32)

---

### Post by jonathan777 on 2009-04-26
Hmm.. it doesn't appear very stable, i'm using a 2 gig flash drive instead.

Can anyone at least tell me if the version of syslinux on the 9.04 CD definitely supports FAT32? (I've heard early versions don't)

I can't believe my laptop bios is having trouble booting from a 4gb FAT32 flash drive..
(A Fujitsu-Siemens Amilo Pa1510)

Thanks.

---

### Post by sgosnell on 2009-04-26
Works for me, with a 4GB Corsair.  It's possible you got a corrupt install on the flash drive.  Try writing it again.  If you used unetbootin under Linux, that may be the problem, because it's a little flaky.  It sometimes takes a few tries before you get a good install.   The best way to do it is to burn the .iso to a CD, then run that and install to the flash drive.  You do need to check the md5sum of the .iso, and then run the check on the CD when it first boots, to make sure you got good files on everything.  One glitch and you've got troubles right here in River City.

---

### Post by jonathan777 on 2009-04-27
That's, what I did - Downloaded the .iso, booted from it, then chose 'create startup disk' option to install to flash. I've tried it a couple of times without success - How to I verify the md5sum of the .iso ?

Thanks for your help!

---

### Post by sgosnell on 2009-04-27
Download the md5sum along with the .iso, and then check that the md5sum matches the computed md5sum of the .iso.  Then, when you boot form the CD, select the option to check the CD.  You can get errors when you download the file, when you burn the file, and when you make the USB OS.  

Ubuntu definitely supports FAT32, but you can use FAT16 if you want.  Either should work.

---

