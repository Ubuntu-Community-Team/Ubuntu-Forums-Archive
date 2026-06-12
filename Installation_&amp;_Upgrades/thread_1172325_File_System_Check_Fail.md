---
title: "File System Check Fail"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by tbresson on 2009-05-28
Everytime I start my computer with Ubuntu 9.04 I get a file system check fail error. It ran fine on 8.10.

I've tried to do a file systems check while it's not mounted. It doesn't report any errors when I do this.

The device is working fine without any problems and is running EXT3. 

Log of fsck -C3 -R -A -a
Thu May 28 16:34:28 2009

```
fsck 1.41.4 (27-Jan-2009)
fsck.ext3: No such file or directory while trying to open /dev/sdc1^M
/dev/sdc1:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by tbresson on 2009-05-30
*bump*

---

### Post by tbresson on 2009-06-02
No one experienced this?

---

### Post by mcduck on 2009-06-02
What filesystem /dev/sdc1 is? Could you post contents of your /etc/fstab here?

---

### Post by tbresson on 2009-06-03
sdc1 is EXT3

Here's my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4fe9b02d-fbef-48b8-b006-935f19afcbb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=6a28598f-8765-4a93-af76-306b7a652684 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1       /home/user/Private        reiserfs        defaults        0       2
/dev/sdc1       /home/user/Other       ext3    defaults        0       2

```

---

### Post by tbresson on 2009-06-11
Could it be that the USB driver hasn't loaded yet and therefore can't access the disk or something?

I guess in the end I'll have to try out a reinstall or perhaps look at Windows 7.

---

### Post by mcduck on 2009-06-11
> **tbresson said:**
> Could it be that the USB driver hasn't loaded yet and therefore can't access the disk or something?

I guess in the end I'll have to try out a reinstall or perhaps look at Windows 7.

So it's on a removable drive? That could be the reason, as some motherboards have the habit of recognizing drives in different order on every boot, and this happens most often when removable drives are involved..

You could try defining the drive in fstab using either UUID or label instead of the device name.

---

### Post by skillllllz on 2009-06-11
> **mcduck said:**
> So it's on a removable drive? That could be the reason, as some motherboards have the habit of recognizing drives in different order on every boot, and this happens most often when removable drives are involved..

You could try defining the drive in fstab using either UUID or label instead of the device name.     

I agree; try using UUID of the removable disk in your fstab. Get the UUID by executing the following command in the terminal:```
blkid
```

---

### Post by tbresson on 2009-06-11
The hardware is the same and I had no problems with the previous version of Ubuntu.

Though I've tried what you both suggested but when I write the command I only get UUID's from my other drives, not the USB disk.

UPDATE: I tried again and I found the UUID and made the changes to the fstab and now it works :D

---

### Post by skillllllz on 2009-06-11
> **tbresson said:**
> The hardware is the same and I had no problems with the previous version of Ubuntu.

Though I've tried what you both suggested but when I write the command I only get UUID's from my other drives, not the USB disk.

UPDATE: I tried again and I found the UUID, how to I write it in my fstab?

in fstab, replace

```
/dev/sdc1       /home/user/Other       ext3    defaults        0       2
```with

```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx      /home/user/Other       ext3    defaults        0       2
```

replacing xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx with the actual UUID of the removable device.

---

### Post by skillllllz on 2009-06-11
Awesome, we're glad to be of help.

Don't forget to mark this thread solved:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

