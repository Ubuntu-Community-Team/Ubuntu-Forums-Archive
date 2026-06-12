---
title: "Mounting The NTFS Drives"
date: 2008-08-23
forum: General Help
---

### Post by Uchiha_madara on 2008-08-23
Hi every one, 
I know this Questions is Classic one .....But I don't know the answer

I removed windows Xp from My Laptop and My Laptop is Pure for Ubuntu !
By Formatting it From the Windows Xp the Live CD and after Formatting 
I shut down The Laptop Immediately


When I need to Configure the NTFS Drives "By using NTFS Configuration tool" Application i gave Me Massage :

> if you have Windows go and Make save remove For the Drive
if you don't have windows make mounting By using -force



How can I mounting in this Situation ?

---

### Post by jerome1232 on 2008-08-23
You probably either hibernated on this drive or just turned off the laptop instead of shutting windows down, which is why it won't mount.

You can try a couple things from the command line to see if it'll mount, but just booting into windows and shutting down would fix it as well.

```
sudo fdisk -l
```

Which ever one says ntfs is the one we are going to use, it'll be like /dev/sda3 or /dev/sdb1 something like that.

```
sudo mkdir /mnt/test
sudo mount -t ntfs-3g /path/to/device /mnt/test -o force
```

if that doesn't work try ntfsfix

```
sudo apt-get install ntfsprogs
sudo ntfsfix /path/to/device
sudo mount -t ntfs-3g /path/to/device /mnt/test
```

once you've mounted it once I think the problem should clear up so try unmounting it and use your configuration tool

```
sudo umount /path/to/device
```

---

