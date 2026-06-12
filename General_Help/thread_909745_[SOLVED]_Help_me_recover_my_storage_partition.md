---
title: "[SOLVED] Help me recover my storage partition"
date: 2008-09-03
forum: General Help
---

### Post by sumpm1 on 2008-09-03
Hi, I am fairly new to Linux. I have my large partition for downloading mounted on /storage. I have a problem though. On a physically seperate hard drive, I XP installed. I wanted to transfer some large files from the XP hard disk onto my ext3 drive that I use for Linux. I COULD have accomplished this from inside of Ubuntu, but with both hard disks connected to IDE, even with ext3 disk as master, the system would still boot to XP. And XP wouldn't recognize the ext3 formatted disk! So I thought maybe there was a file browser on a GParted CD that I had laying around. But once that CD ran, I realized that there was no file browser on that cd. SO I tried copying and pasting the ENTIRE PARTITION from the XP disk to the ext3 partition within Gparted. Gparted gave me an error very quickly.

Now when I boot Ubuntu, the /storage partition is not mounted, and will not mount. I use this command in terminal:
```
sudo mount /dev/sda4 /storage
```

and get this error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm not exactly sure what to do now. Gparted shows that the partition still contains all of the original data(that it is half full). And it seems that the superblock may be bad (not that I really know what a superblock is!).

Help me please, I don't want to lose all of the data on that partition.

---

### Post by Gannon8 on 2008-09-03
What was the partition formatted as? If it was ext3, than you can use:
```
sudo fsck.ext3 /dev/sda4
```
And have the command check it.

Or you can right click the partition in GParted and select check.

---

### Post by sumpm1 on 2008-09-04
> **Gannon8 said:**
> What was the partition formatted as? If it was ext3, than you can use:
```
sudo fsck.ext3 /dev/sda4
```
And have the command check it.

Or you can right click the partition in GParted and select check.

I used check from the right click in Gparted and that did the trick. Linux is tricky, but it is worth the tinkering to have OS stability, and few viruses. And it's really nice to have experienced helpful users around too. Thanks for the help Gannon8!

---

