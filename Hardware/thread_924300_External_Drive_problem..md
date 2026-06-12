---
title: "External Drive problem."
date: 2008-09-19
forum: Hardware
---

### Post by XtremeGamer99 on 2008-09-19
I recently got a 500GB external drive and an enclosure case for it. It's hooked up to my computer via e-sata.

I'm having a problem booting into linux when it's turned on. When it's on while booking, the boot process hangs at Mounting Root Filesystem (or somewhere around there). I think it's because the assignment of the drive interferes with the assignment of the permanent drives of which I have linux stored on. For example, when booting up, I think it's assigned sdb (which is my linux hdd) rather than sdc like I would think (and does so when turned on from linux), and the boot process tries to look into the external drive for the linux partition and can't find it. That's the way I see it, but it could be another problem.

I would really like to keep this drive powered on at all times. I dual-boot into XP also, and for some reason it isn't hot-swappable in XP so it has to stay on during boot, which conflicts with booting into linux, thus making likfe confusing making sure it's either off/on depending on which OS I'm going into. 

Thanks!

---

### Post by timcredible on 2008-09-19
yeah, you're probably right - the external drive must be reporting in before the in-case drive.  the easiest solution is to reinstall ubuntu so that the installation gives you the option of which drive to install ubuntu on and which one to use as a data drive.  if that's a lot of effort, then you'll need to find out which drive is being reported as what and modify your /etc/fstab accordingly.

---

### Post by XtremeGamer99 on 2008-09-19
I've confirmed that the mobo is registering it before anything else. I'd rather not reinstall anything. Nor edit the fstab file. Because if I were to edit the fstab file, and then have the external drive off for some reason before booting, then I'm stuck in the same situation. It will be on most of the time, but there will be times when I manually turn it off for various reasons.

I was thinking about using drive IDs. I can't remember what they are called exactly or how to use them, but they take a unique id that IDs a particular partition, and use that, no matter what letter the drive is. Can someone give more info?

---

