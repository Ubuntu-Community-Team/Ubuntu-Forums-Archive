---
title: "Seagate 250 GB external hard drive turns to read-only"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by checkeredshawn on 2007-12-04
First of all, the drive does not automatically mount when I plug it in like it used to.  
Second of all, I have to mount it myself using sudo mount /media/Seagate
Third and worst of all, the filesystem turns to read-only randomly; it seems to happen when it is plugged in for a long time.
Also, my Kingston Datatraveler thumb drive will not mount automatically unless the external hard drive is already mounted.  

I got this output from dmesg:

[ 4394.192000] lost page write due to I/O error on sdb1
[ 4483.044000] ext3_abort called.
[ 4483.044000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal

One more thing: when I formatted the drive to ext3, it showed over 11 GB of space taken up when it was completely empty.  The .Trash directory also had nothing in it.

Edit: f2sk gives this message: 

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Is a directory while trying to open /media/Seagate/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by dasunst3r on 2007-12-04
What you are describing would be grounds for replacing the drive.  Back up everything you have on there and try reformatting the drive (if you want to see if the drive is still good by any chance).

---

### Post by checkeredshawn on 2007-12-04
I've tried this before and have gotten the same problem.  Should I use gparted to format the drive to ext3?

---

### Post by dasunst3r on 2007-12-04
Do you have everything backed up elsewhere?  In my three years of using Linux, whenever a filesystem remounts itself read-only, it means something is about to go HORRIBLY wrong.  In any case, you would indeed want to try reformatting your external hard drive EXT32.

---

### Post by checkeredshawn on 2007-12-05
The data on the hard drive is not important to me, but getting it working is.  Is ext32 a filesystem or was that a typo?

---

### Post by dasunst3r on 2007-12-05
Whoops!  EXT3 is what I meant.  I think I mixed up FAT32 and EXT3.  :lolflag:

---

### Post by DizzyTech on 2007-12-05
***STOP!***

This is supposed to happen!  After 15 min of idleness, Seagate drives go into sleep.  However, Linux "probes" connected devices every couple of seconds.  The drive only wakes up when you write something to it.  Therefore, the Linux driver starts screaming and remounts it as readonly.  This is not a sign of a failing drive, nor do you need to partition it.  All you need to do is remove it when you're not using it.

---

### Post by dasunst3r on 2007-12-06
Thanks for that, DizzyTech!  Does that still hold true for their FreeAgent line?

---

### Post by DizzyTech on 2007-12-06
Yes, in fact, I found this out using a FreeAgent drive (I put Feisty on it when my lappy's hard drive started to up and die)

---

### Post by checkeredshawn on 2007-12-08
[http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/](http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/)

---

### Post by petterth on 2007-12-14
Hi Guys!!
I'm having the same problems only with my root filesystem "/" it turns into read-only and i'm not able to open any programs anymore, after a restart it's all good again but after about 30 minutes of use it's back to read only, what could be wrong?

---

