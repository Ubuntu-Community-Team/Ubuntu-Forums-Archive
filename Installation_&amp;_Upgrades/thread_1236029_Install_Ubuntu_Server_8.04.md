---
title: "Install Ubuntu Server 8.04"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by User Dude on 2009-08-09
I have been trying to install Ubuntu Server for a while now and have had no luck with it what so ever. I have tried 3 different machines so far and have not gotten a bootable system yet. The first two (a quad Pentium III and a Athlon XP) were at least 7 years old and I figured were too old to be supported. However, the last machine I tried to install on was an Athlon 64, and only about 4 years old. I got similar results with all 3 machines. 

When I run the install CD, it runs to the end and the system reboots to start the new OS, at that point, it refuses to boot the Ubuntu system. If anyone can help, I still have the latest system put together and can work on getting it working. The first 2 tries have been dismantled and put to other uses so I cannot answer many question about them.

When the system quits booting, it drops to a shell and gives an initramfs prompt. Before dropping to the shell it says it is booting from hd0 (zero) and gives a error message about giving up waiting for root devices. Says to check boot args rootdelay and root in /proc/cmdline. When I look here in the cmdline file, there is no args by this name and the only line there is to the UUID followed by a long file name that looks like a string of random alpha numeric characters. 

Then there is an "Alert! /dev/disk/by-uuid/ (the above mentioned string of random alpha-numeric characters) does nor exist, dropping to shell" message.

When I use a live CD and look into the /dev/ folder I do not find a hd0 or any other hd anything. Also, since I am using a SATA disk I expect to find a sda file, which is not there either.

Also, I am using the 32 bit server 8.04 for all installations.

System parameters of interest:
Mobo:Chain tech
CPU: Athlon 64
Hard Drive: 120 Gig SATA

Does anyone have any suggestions?

---

### Post by aysiu on 2009-08-10
Maybe there's something wrong with the CD you're using to install Ubuntu.

Maybe it got corrupted during the download or during the burning process.

---

### Post by User Dude on 2009-08-10
> **aysiu said:**
> Maybe there's something wrong with the CD you're using to install Ubuntu.

Maybe it got corrupted during the download or during the burning process.


Hey, Thanks for the reply. Good thinking, the disk is the common link between all installations.

I just completed a CD check and it completed successfully. So the disk is not the problem.

---

### Post by phillw on 2009-08-10
I'd still be tempted to download and burn a new cd at X4 ...  Seems most odd that none of your machines are happy with it.

Phill.

---

### Post by User Dude on 2009-08-15
Hey Phill, Thanks.
I downloaded the new server release and burned it and it worked. So it probably was a bad disk that still passed the built in test. 

Thanks

---

