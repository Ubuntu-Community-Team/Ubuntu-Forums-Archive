---
title: "Error installing video card"
date: 2009-10-25
forum: Hardware
---

### Post by Chrisk1152 on 2009-10-25
I have a SLI linked Geforce 9800 GT video card and I downloaded the drivers for it (Linux x64)  When I goto run it I get a message:

ERROR: nvidia-installer must be run as root


How can I do this?  I have searched the forums and online docs for how to run something in root but have found nothing.

---

### Post by IcarusR on 2009-10-25
Type 'sudo' before the command & enter your own user password when asked for it.

Something like this...
```
andy@Florence:~$ sudo fdisk -l
[sudo] password for andy: 

Disk /dev/sda: 1000.2 GB, 1000203837440 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001243f

```

---

