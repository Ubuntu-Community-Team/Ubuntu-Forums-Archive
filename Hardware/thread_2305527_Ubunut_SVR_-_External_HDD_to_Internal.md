---
title: "Ubunut SVR - External HDD to Internal"
date: 2015-12-06
forum: Hardware
---

### Post by Ranvens on 2015-12-06
Hi All,

I have an odd issue, I wanted to reduce cable clutter on my desk, so I removed the HDD from my external HDD case and installed it into one of my HP MicroServer bays. It is a WD Green. 
The HDD is detected when doing an LSHW however it is showing an inconsistent total size. It was showing that either the partition table or the superblock has become corrupt.
Drive is formatted in ext4.
However, when I reconnect it to the external HDD Caddy and plug it back in via USB, everything works perfectly again and it mounts with no issues. 

Is there any way that I can get this working?

---

### Post by TheFu on 2015-12-07
If data loss isn't an issue, repartition the drive, reformat with ext4, then use that backup you have to copy any important data back.

Seems WD wanted to prevent folks from doing this (USB disks are almost always cheaper than plain drives because a 90 day warranty cost them less than a 2 yr warranty) so they did something funky with the USB controller. That's just a guess. I don't really know. I know that other USB drive controllers do stuff like this.

Did you do a web search for solutions to this issue already?  What have you tried?
[http://www.tomshardware.com/forum/293943-32-drives-moved-enclosure-unpartitioned-space](http://www.tomshardware.com/forum/293943-32-drives-moved-enclosure-unpartitioned-space) seems related, but they are Windows users.
and
[https://superuser.com/questions/434877/how-can-i-retrieve-data-from-a-western-digital-passport-external-disk-which-is-n](https://superuser.com/questions/434877/how-can-i-retrieve-data-from-a-western-digital-passport-external-disk-which-is-n)

Hopefully those explanations lead you to a solution, but backup, format, restore seems the easiest.  Plus it will remove a sketchy USB-to-SATA bridge from the equation.

---

