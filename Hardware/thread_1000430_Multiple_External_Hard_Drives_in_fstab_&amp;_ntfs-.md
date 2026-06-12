---
title: "Multiple External Hard Drives in fstab &amp; ntfs-config"
date: 2008-12-02
forum: Hardware
---

### Post by Rosend on 2008-12-02
I have two external hard drives. One is ntfs, the other is vfat.
I want to be able the mount either one at any given time.
Right now, I have an entry in fstab for sdb1, as vfat, and I'm using ntfs-config to mount the ntfs hard drive. BUT, if I try to mount the ntfs drive without already having the vfat one mounted, it reads as sdb1, and I get an error message and have to mount the drive manually.

So, is there a way of editing my fstab file so that I can turn the drives on in whichever order and still have them mount properly?

---

### Post by jpkotta on 2008-12-04
Each hard drive partition has a (or can be given a) UUID.  Get the UUID with ```
sudo vol_id /dev/sd*XY*
```

---

### Post by falcon61102 on 2008-12-04
Also, what you can do is specify the mount point for the drive that you have in the fstab that way it will mount no matter what else is mounted.

First, create a new directory for the mount point with:
```
sudo mkdir /media/External
```
Where External is the name of the new folder.

Now open up your fstab and change the mount point for your drive.  Recommend that you also use the UUID like jpkotta recommended.
The line in your fstab should look something like this:
```
# /dev/sdb1
UUID=XXXX-XXXX    /media/External   vfat.... 
```

By specifying the UUID and the mount point for each drive, you will be able to avoid confusion and any links to locations on those drives will remain good no matter what configuration of drives you have running.

---

