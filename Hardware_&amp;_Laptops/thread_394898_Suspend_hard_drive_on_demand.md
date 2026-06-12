---
title: "Suspend hard drive on demand"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by kitman420 on 2007-03-27
I have an ubuntu linux system with 2 hard drives. One is my main OS/working drive, and the other is a backup drive. I want to manually turn off one of the drives for most of the day, then, when I am ready to do a backup, I will turn the drive back on and do the backup.

The best way of doing this seems to be with hdparm. hdparm has 2 switches to power down a drive: -y and -Y. 

According to the man page, -y puts it in standby and -Y puts the drive in sleep mode. I tried using -Y but it didn't work.

My main goal is to increase the lifespan of the backup drive by keeping it powered off unless I need it.  Any suggestions.

Thanks.

---

