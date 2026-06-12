---
title: "cdrom"
date: 2008-09-01
forum: General Help
---

### Post by wfp on 2008-09-01
Just wondering having a problem mounting cdrom get this error message from console> wayne@waynes-desktop:~$ sudo mount /dev/cdrom0
[sudo] password for wayne: 
mount: can't find /dev/cdrom0 in /etc/fstab or /etc/mtab

Heres a copy of fstab> # /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# 
/dev/sda1
UUID=066ac81e-d42c-4602-9c82-37524bc12c9f /               ext3    relatime,errors=remount-ro 0       1

 /dev/sda5
UUID=b2985951-e96d-4bb8-bba4-323f348f80fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by eggdeng on 2008-09-01
> /dev/cdrom0
Your syntax is wrong. You mount a device (in this case, /dev/scd0) to a folder (/media/cdrom0)
So, it should be
```
sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by wfp on 2008-09-01
sudo mount /dev/scd0 /media/cdrom0
[sudo] password for wayne: 
mount: special device /dev/scd0 does not exist

---

### Post by Sycron on 2008-09-01
```
sudo mount /dev/cdrom0 /media/cdrom0
```
I'm not sure it works.

---

### Post by eggdeng on 2008-09-01
If that fails, you could try 
```
sudo mount /dev/cdrom /media/cdrom0
```
```
sudo mount /dev/sr0 /media/cdrom0
```
or just browse your /dev folder 
```
ls /dev
```
to see if you can find the device name. (One of the blue entries).

---

### Post by wfp on 2008-09-02
Had the same issue about a week ago. Playing cd in drive was scratched took the cd out, then ubuntu could not find my cdrom. I opened my box disconnected drive, reconnected and booted and ubuntu found my cdrom. Same thing this week playing a scratched cd it started to skip took the cd out, lost drive. Tried the same thing as last week but ubuntu can not find drive. Now i am thinking it's just a bad drive, and maybe time for new one. Thanks for all your replys. I guess whats bothering me is that it happened both times with a scrached cd in drive maybe just a fluke. Maybe i need to take better care of my cd's lol.

---

