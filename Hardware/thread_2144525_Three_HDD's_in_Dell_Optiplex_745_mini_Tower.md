---
title: "Three HDD's in Dell Optiplex 745 mini Tower"
date: 2013-05-12
forum: Hardware
---

### Post by NIMDog on 2013-05-12
Hi all! I am wanting to use three hdd's in my pc, which is running 13.04. However, I am not sure how to set ubuntu up to use the two extra hdd's. Any advice?

---

### Post by ajgreeny on 2013-05-12
I presume U 13.04 is on the first disk and you want the two new ones as storage.  Do you also run Windows or will these new disks be needed only for Linux, as that will affect the format type you need to use; ext3 or ext4 for Linux, but NTFS if you need them for both OSs.

Once you have them formatted and installed run ```
sudo fdisk -l
sudo blkid -c /dev/null
``` and report back here with the output from those two commands and we can halp you get them to mount at boot time and be available for your use.

---

### Post by NIMDog on 2013-05-13
Actually I was wanting to create a RAID 5, but all the other explanations don't seem to work! Apparently, the install disk gives you a option during the partition section where you can create a RAID, but I look for the "Physical Volume for RAID" option and it doesn't exist on 13.04. Very frustrating. With the easy way not working, the difficult way (terminal) doesn't seem to want to work for me either. This is really frustrating. Why can't there be a easy way to do this? It seems that it would be something that a lot of people would like to do but they can't because it is too complicated!

---

