---
title: "I want to re format"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by red777 on 2007-04-24
a secondary slave drive, currently formatted  NTFS. It is mounted & I can see all files on it but they are read only files.There's nothing on it I want to keep so how do I format it, I'm using UBUNTU 7.04

---

### Post by BoneKracker on 2007-04-24
You will probably prefer to do this with a graphical tool.  You can install a graphical tool called "gparted" that makes managing disk partitions and filesystems much easier for people new to Linux.

What you want to do is use gparted to delete any existing partitions on that disk, create one or more new ones, set the format of those new partitions to "ext3", and then apply the changes.  Then, to set up that new partition (or partitions, as the case may be) for use, you can use some simple commands in terminal.

First, create a mount point for each of those partitions (for example - suppose you'd like to have a separate place for your photos and other stuff):
```
sudo mkdir /media/storage
sudo mkdir /media/photos
```
(delete any extraneous mount point(s) that pertained only to the disk as it had been set up (like say /media/windows or /media/ntfs or whatever))

Then, put an entry in /etc/fstab for each of those partitions:
```
sudo gedit /etc/fstab
```
Delete any existing lines that pertain to this disk, and add something like the following.
```
/dev/hdb1          /media/storage         ext3                user,noauto,noatime        0   0
/dev/hdb2          /media/photos          ext3                user,noauto,noatime        0   0
```
(with the correct device names, and mount points)

Save the file.

If you want to be consistent with Ubuntu's new use of UUIDs instead of device names in /etc/fstab, then you'll want to replace the "/dev/hdb1" and "/dev/hdb2" above with the correct UUIDs.

You can look up the correct UUIDs for those devices like this (it's probably a good idea to reboot first, to make sure these are up-to-date with new partitions):
```
ls -l /dev/disk/by-uuid
```
You'll see something like this (but probably shorter):```

lrwxrwxrwx 1 root root 10 2007-04-24 01:16 3b35f56c-c8ce-4582-954f-909ebd9cc520 -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 4d865933-dfcb-45a4-98b8-405315b2dc3d -> ../../hda7
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 5796fb0f-455b-47c9-9c8a-d637aa063e9e -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 89ebfd5e-666a-4ed1-9165-c89ae087e0e8 -> ../../hdb4
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 909c2e4a-2297-461b-bcf9-20e1f48cdc7f -> ../../hda9
lrwxrwxrwx 1 root root 11 2007-04-24 01:16 91f0832b-ed49-46fc-a813-24c997b97a97 -> ../../hda10
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 b4ceed44-36df-4278-b9b1-de946246b3c4 -> ../../hdb3
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 b7b40405-89fd-4a32-8803-147e6b2749ec -> ../../hda8
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 de37f0af-a49d-4d27-bbe0-6f50cce3370b -> ../../hda4
lrwxrwxrwx 1 root root 10 2007-04-24 01:16 f12982d5-14f1-42eb-b020-fc4cb1fc6c3d -> ../../hda6
```

Look for your device(s) on the right.  The UUID is the part preceding it (between the time and the little arrow "->".

In /etc/fstab, you can safely just have "default" for the mount options, in which case those partitions will automatically get mounted at boot time (and in which case the second "0" should be a "2").  The mount options I've suggested ("user,noauto,noatime") will let any user mount the partitions when they want to use them (there will be little disk icon for each inside "Computer").  Noatime just makes it a little quicker because you probably won't need the time last accessed.  You can read more about the power of mount options by typing into the terminal "man mount".

---

