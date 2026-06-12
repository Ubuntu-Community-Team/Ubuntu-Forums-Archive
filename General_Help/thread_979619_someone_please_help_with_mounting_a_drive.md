---
title: "someone please help with mounting a drive"
date: 2008-11-12
forum: General Help
---

### Post by redbull816 on 2008-11-12
i have only used linux for about 3 hours in my entire life so i have no clue what i'm doing. when i plug in my external drive it says that it can't mount because ntfs is being used. what am i doing wrong?

---

### Post by geirha on 2008-11-12
NTFS has a flag that says "I'm in use". It is set when windows mounts it, and it is unset when it properly unmounts it (E.g. with the Safely remove harddrive feature). It sounds like it has this flag set at the moment, which means it wasn't properly unmounted (perhaps unplugged without doing safely remove harddrive, or if windows was uncleanly shutdown while the drive was mounted). The easiest way to fix that is to connect it in windows, and have windows properly unmount it.

---

### Post by redbull816 on 2008-11-12
thank you for your help. unfortunately i deleted windows..

---

### Post by kpkeerthi on 2008-11-12
Can you see if [ntfsfix]("http://man.linux-ntfs.org/ntfsfix.8.html") helps repair the problem? In most cases it does.

1. Install ntfsprogs
```
sudo apt-get update && sudo apt-get install ntfsprogs
```
2. Get the device name using 
```
sudo fdisk -l
```
I assume your NTFS drive is **/dev/sdb1**
3. Run ntfsfix utility on your NTFS drive
```
sudo ntfsfix **/dev/sdb1**
```
* Change /dev/sdb1 to whatever applies to you
4. Disconnect the drive and re-connect

---

