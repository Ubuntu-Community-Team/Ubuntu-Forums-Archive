---
title: "gddrescue help"
date: 2013-08-19
forum: Hardware
---

### Post by TurkVU on 2013-08-19
Trying to recover data from a raid array with gddrescue and could use some help.

I installed the two disks in my system and used disk utility to start the array (/media/raiddisk)

I then mounted a NAS that I'd like to create the image on (/media/Data)

When I run:

```
sudo ddrescue -n -f /media/raiddisk /media/Data logfile
```

I get:

```
ddrescue: Can't open output file: Is a directory
```

What am I doing wrong?

Also, should I try running Check Filesystem from Disk Utility before running gddrescue? Not sure if this is advisable on a raid setup

Thanks for any and all assistance.

---

### Post by TurkVU on 2013-08-20
Figured this out - updated code:

ddrescue -n /media/raiddisk /media/Data/image.img /media/Data/logfile

---

