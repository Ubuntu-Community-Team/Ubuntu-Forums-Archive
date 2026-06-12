---
title: "Problem mounting 1 NTFS partition"
date: 2008-08-29
forum: General Help
---

### Post by papa0tter on 2008-08-29
I have 5 NTFS drives all mounted and useable but just cannot get the second partition on one of the drives to mount/work. The first partition is mounted and accessible but the second partition of this drive refuses to budge.

I have installed, reinstalled and removed ntfs configuration and nothing has changed. All drives remain the same. Please help as this partition has most of my music and I have run out of ideas.

I am a linux newb but have put in about 2 days work trying to get this thing to mount.

Using Hardy Heron 8.04, everything worked fine before the upgrade.

Help me ubuntu forum, your my only hope!

---

### Post by kpkeerthi on 2008-08-29
Run these commands in a terminal and post back the errors:
```

sudo mkdir /media/MyDisk
sudo mount -t ntfs-3g [COLOR="Red"]**/dev/sda1**[/COLOR] /media/MyDisk

```

**Note: **Change [COLOR="Red"]**/dev/sda1**[/COLOR] to appropriate device as applicable to you. You can find the device name using```
sudo fdisk -l
```

---

### Post by papa0tter on 2008-08-29
I think it kinda worked but maybe I mounted the wrong disk?

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30400   244187968+   7  HPFS/NTFS
futak@ubuntu:~$ sudo mkdir /media/MyDisk
mkdir: cannot create directory `/media/MyDisk': File exists
futak@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdf1 /media/MyDisk
fuse: mount failed: Device or resource busy

I typed in what you said but failed to change the drive in your note the first time. So the files in the new directory appeared to be linked to files from a different drive.

This stuff is still very confusing for me.

---

### Post by kpkeerthi on 2008-08-29
Change it to as below since you already have another partition mounted to /media/MyDisk

sudo mkdir /media/MyNTFSDisk
sudo mount -t ntfs-3g /dev/sdf1 /media/MyNTFSDisk

---

### Post by papa0tter on 2008-08-29
Thank you, that worked. But still for the wrong disk. 

I need a do over button as I think I am messing up this install.

---

### Post by papa0tter on 2008-08-29
IT WORKED!

Thank you, I tried messing around some more with fdisk -l and found I was just using the wrong (drive letter)?

Anyways it is now mounted thanks so much for the help kpkeerthi!

I owe you a beer.

---

