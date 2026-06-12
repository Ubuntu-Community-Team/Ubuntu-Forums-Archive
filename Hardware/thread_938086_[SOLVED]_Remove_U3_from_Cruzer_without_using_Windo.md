---
title: "[SOLVED] Remove U3 from Cruzer without using Windows"
date: 2008-10-04
forum: Hardware
---

### Post by rubenverweij on 2008-10-04
Hello everyone,
I have a 2GB Cruzer SanDisk USB stick with U3 software on it. The problem is that the U3 software is utterly annoying! I now about the u3.com/uninstall approach, but this won't work for me: the only Windows computer I have access to has no administrative rights.
I tried to repartition and reformat it in GParted, but GParted won't see the CDFS partition the U3 software is on. :(
Does anyone have a suggestion what to do?
Ruben

---

### Post by OptikKnight on 2009-01-26
Hi, did you ever find a solution to this? Please post it if you did!

Thanks!

---

### Post by rubenverweij on 2009-01-26
No, sorry, I just found a windows pc and downloaded the uninstaller...
Maybe you could try to run the program in Wine or VMWare?

---

### Post by genfinch on 2009-12-30
hi admins
could you please remove the [solved] tag? the crashing disappointment after the tingle of hope when you see it on google is really depressing... :'(
thanks

---

### Post by cyberdo on 2010-10-04
Running:
```

sudo u3-tool -p 0 /dev/sdb

```
seemed to work for me

---

### Post by malspa on 2010-10-04
Did they stop putting that U3 crap on their flash drives?  Got a new one last month (SanDisk Cruzer Micro Skin 4GB), picked it up because it only cost $5.  Finally plugged it in when I saw the latest post in this thread, but all I see is a single FAT32 partition.

---

### Post by larubbio on 2010-12-28
Rather than run the command cyberdo posted, I would suggest looking in /etc/mtab to see where the usb drive is mounted and then use u3-tool on that device.  You can also run 

```
u3-tool -i <device>
```

before using -p to see how it is currently configured

---

