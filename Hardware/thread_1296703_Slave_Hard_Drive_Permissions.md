---
title: "Slave Hard Drive Permissions"
date: 2009-10-21
forum: Hardware
---

### Post by mem0rex on 2009-10-21
Well I just setup a slave drive and it is not letting me change anything on the Slave. I cant add files or delete it just says Permission Denied... Let me give you so info on the HD it was an old Maxtor 10 GB, it has Ubuntu installed on it now. (I don't know if this is a problem) I want to wipe it clean and use it for extra space. I ran "sudo fdisk -l" and got the following:

```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf52bcf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4863     1502077+   5  Extended
/dev/sda5            4677        4863     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aabe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1158     9301603+  83  Linux
/dev/sdb2            1159        1216      465885    5  Extended
/dev/sdb5            1159        1216      465853+  82  Linux swap / Solaris
```Can anyone please help me with this?

---

### Post by scragar on 2009-10-21
```
sudo apt-get install gparted
```
Run **g**nome **part**ition **ed**itor from the system tools menu(I think), then in the drop down(top right) choose the second HD, delete all partitions, create a new one using the freed space and make it fat32.
Click apply(top left).
Wait.
When it's done remount the drive(I think ubuntu normally does this by default) to access your new space.

---

### Post by mem0rex on 2009-10-21
Thank you very much, it worked like a charm. :)

---

### Post by scragar on 2009-10-21
I don't know if this is in the current ubuntu release, so you might have to ignore what I say here and move onto lower down, but under System Tool there may be a program called disk manager.
If your second hard drive doesn't appear in places it should work in there.

If your hard drive doesn't appear in either place, then it's time to start editing thing.
```
sudo blkid | grep sdb1
```
That will show the UUID for the second hard drive, so let's add this to FSTAB:
```
sudo nano /etc/fstab
```
At the very end insert this line:
```
UUID=**THE_UUID_GOES_HERE** /media/**HD2** vfat sync,nodev,nosuid,user,rw,auto 0 1
```
Be sure to use the right UUID(without quotes) and change HD2 to anything you want(as long as you can remember it and it doesn't have spaces or tabs).
ctrl+o to write it out, don't change the file name. ctrl+x to exit.
After that we need to create a new directory for the mount point:
```
sudo mkdir /media/**HD2**
```
And finally mount the drive(if this works it should now be automatic on boot):
```
mount /dev/sdb1
```

---

### Post by mem0rex on 2009-10-21
Why do I need to do all that?

---

### Post by scragar on 2009-10-21
OK, in order it:
```
sudo blkid | grep sdb1
```
Finds the unique ID for the hard drive, so if you re-order the hard drives you don't have to worry about it.

```
sudo nano /etc/fstab
```
Modify the **f**ile **s**ystem **tab**le so linux can automount it.

```
UUID=**THE_UUID_GOES_HERE** /media/**HD2** vfat sync,nodev,nosuid,user,rw,auto 0 1
```
This line essentially just get's it ready for easy use, HD2 is what it shows up on the desktop as, vfat is the format, sync-noauto are options, essentially you want changes to be wrote immediately to disk(sync), no perms problems(nodev, nosuid + user), read write(rw) and automaticly mount at boot(auto).

```
sudo mkdir /media/**HD2**
```
Create the folder that the contents will appear in on your file system.

```
mount /dev/sdb1
```
Mount it now to save having to reboot for it to appear.

---

