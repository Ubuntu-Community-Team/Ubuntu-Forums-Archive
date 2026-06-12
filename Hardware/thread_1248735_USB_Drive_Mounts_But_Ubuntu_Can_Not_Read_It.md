---
title: "USB Drive Mounts But Ubuntu Can Not Read It"
date: 2009-08-24
forum: Hardware
---

### Post by umechanism on 2009-08-24
I'm using Ubuntu 8.10 and I have a 3.5" external hard drive that I connect to my computer via USB.  It has been working just fine up until a week ago.  Now, when I plug it in, it mounts (I think), the disc starts spinning (I can hear it and see the LED blinking), but I can not read from the drive at all.  I've plugged it into a Vista machine, XP machine, and a Linux machine and none of them can read it but they all can mount it.  Even in Windows, when I plug it in, I get that "USB device found" & "Installing Hardware Drivers" then "Your Device Is Ready To Use" messages.

Any idea what is going on? 

Thanks!

---

### Post by recluce on 2009-08-24
I would probably try to install one of the numerous hard drive data recovery tools under windows. They all have "trial versions" that will assess the condition of your data and tell you if/what they may be able to recover. To actually recover any data, you will have to pay $$$. Since these tools work read only on the broken drive, it will at least tell you if there is still any readable data there or if the drive is FUBAR.

All this is assuming that you are talking about a FAT or NTFS formatted drive.

---

### Post by jerrrys on 2009-08-24
do you know about this?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by umechanism on 2009-08-24
> **jerrrys said:**
> do you know about this?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Ok, I used TestDisk to check my drive.  This is the result:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdf - 85 GB / 79 GiB - CHS 81705 64 32
Analyse cylinder  1085/81704: 01%
Read error at 1084/2/1 (lba=2220096)


```

Any idea what this error is or if there is a fix for it?

---

