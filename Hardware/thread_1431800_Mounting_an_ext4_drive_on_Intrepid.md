---
title: "Mounting an ext4 drive on Intrepid"
date: 2010-03-17
forum: Hardware
---

### Post by fontenot_1031 on 2010-03-17
Hi, I'm still on Intrepid because I want to use the proprietary drivers for my graphics card which was dropped after Intrepid.
Anyway I have an ext4 partition on my computer from my last install and I want to be able to mount it on Intrepid without having to move all the data off of it and formatting it to ext3. What are my options?

---

### Post by khelben1979 on 2010-03-17
Locate the harddrive on the disc:
```
df -h
```

Mount your harddrive partition to a mountpoint on the disc (where sda would be changed to your choice):
```
mount -t ext3 /dev/[sda] /mnt/
```

Change to the mounted directory:
```
cd /mnt
```
where you can copy the files from the partition you need to keep.

---

### Post by fontenot_1031 on 2010-03-17
```
david@hpdv5000:~$ sudo mount -t ext3 /dev/sda2 /mnt/datadisk
mount: wrong fs type, bad option, bad superblock on /dev/sda2
```

Would I have a hardtime building a new kernel with ext4 support?

---

### Post by needhelpplease on 2010-12-25
You can do it.  I had to do it just now, because I'm backing up an old server onto an external disk and the only external disks I have are ext4.

The trick to it I found is here: [mounting ext4 on intrepid]("http://pabloseminario.com/2009/07/01/ext4-support-in-ubuntu-intrepid-8-10/").  The key command to look at there is using the tune2fs -E test_fs /dev/sd__ to enable experimental FS mods.

I have no idea how reliable this is.  I hope it works well enough that I can get the files off securely, that's all.

---

