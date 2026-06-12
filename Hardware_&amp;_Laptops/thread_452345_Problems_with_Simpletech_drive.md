---
title: "Problems with Simpletech drive"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by gamer_pro_2000 on 2007-05-23
Alright everyone.  I'm having problems with both my 180gb external Western Digital Hard drive and my SimpleTech 40 gb external in Ubuntu 7.04 Fesity Fawn.  I installed the OS, and it was great for a very long period of time.  I installed ntfs-3g with the NTFS configuration utility, and it seemed to function just as it said it would, although I could not write to external storage, only internal.  I modified the settings in the configuration utility to allow external as well, but now my drives that are external don't automount.  I have to completely restart for them to even show up in the Places-->Computer and sometimes they show up, others they don't.  My internal partition with my Windows on it is fine.  It reads and writes like a champ, but my external storage is a gamble.  I have to restart several times before it finally decides to recognize it, and even when it does, sometimes it says $logfile is corrupt, please boot into Windows and safely remove, which I do and then it does not show up at all again.  I dunno if this is a problem with ntfs-3g or some program I have installed that is conflicting with it.  Anyone got an idea?  BTW, I'm using an Acer Aspire 5100 series notebook with ATI graphics and AMD Turion 64 X2.

---

### Post by gamer_pro_2000 on 2007-05-23
*Bump*

---

### Post by gamer_pro_2000 on 2007-05-23
*Bump again*

---

### Post by prince_niceguy on 2007-08-20
there seems to be a bug and i had to manually mount my external drive using following code.

$ pmount-hal /dev/sdb[drive number]

you can get the drive number using gnome partition manager or some other partition manager. Just substitute the same and you should be all set.

Hope that helps.

---

