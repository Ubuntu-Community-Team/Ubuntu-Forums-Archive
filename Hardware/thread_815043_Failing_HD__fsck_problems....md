---
title: "Failing HD?  fsck problems..."
date: 2008-06-01
forum: Hardware
---

### Post by ZAxisMapping on 2008-06-01
I was hoping to get some help from the filesystem/harddrive gurus here, as I'm afraid I'm reaching the boundaries of my knowledge.

Basically, I've got a failing WD Rapter SATA drive on my hands (after an incredibly stable run with Fiesty) - or a severely corrupt ext3 filesystem - I'm not positive which.  SMART analysis suggests the drive is failing.

Luckily, I was able to install a fresh copy of Hardy on a functioning drive - so I've got a clean, stable OS drive to play with my failing drive.

Essentially, I was getting the following errors (sorry, this output is from my notes):

```
EXT3-fs error
device sdb1 ext3_get_inode_loc: unable to read inode block inode=..., block=...

```

and a repeated cycle of:

```
SRST failed (errno=-16)
COMRESET failed (errno=-16)

```

I also received:


```
EXT3-fs corrupt root inode, run e2fsck

```


From various threads with similar errors, I guessed (hoped) it may be an issue locating a superblock.  I installed TestDisk ([cgsecurity.org/wiki/TestDisk_Download]("http://cgsecurity.org/wiki/TestDisk_Download"))
and re-ran fsck with the superblock data return from TestDisk:

(failed disk is NOT mounted when I run fsck - partly b/c it can't be mounted)

```
$sudo /sbin/fsck.ext3 -b 32768 -B 4096 /dev/sdb1
ext3 recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sdb1: recovering journal
/sbin/fsck.ext3: No such device or address while trying to re-open /dev/sdb1
Segmentation Fault
$

```

My entire machine locked up at this point - which is partly why I have not included perfect copy/paste output here.  The desktop is quite unstable with the failed drive in place.


So, I'd obviously like to recover the files on the drive.  Any ideas/general thoughts would be appreciated!  To summarize:

I.  In general, 'sudo lshw' recognizes the disk and it's partitions when I first boot into gnome.  Hence, commands with '/dev/sdb1' agruments are recognized, but typically fail.  

II.  I attempt to mount the drive into /mnt/ and mount hangs at the terminal prompt.  I can't even ^C it.

III.  It's looking like the low-level linux apps are failing on this drive, is my only hope some type of recovery analysis though an app like TestDisk?  If so, any specific suggestions??  Thanks!!

---

### Post by ZAxisMapping on 2008-06-01
I've downloaded the WD "Data Lifeguard Diagnostic for DOS (CD)" - I boot into it and it gets no where because of the SMART errors.

If it helps, it highlights:

```

ID: 5
Name: Re-allocated Sector Count
Value: 70
Thresh:  140
Worst: 70
```


The software does not attempt any recovery, and forces me to reboot at this point.

Is there any hope of recovering the data from the drive?  Thanks!

---

### Post by ZAxisMapping on 2008-06-03
I've moved this thread to this forum, as it might be more appropriate under hardware.  

I was hoping to get some help from the filesystem/harddrive gurus here, as I'm afraid I'm reaching the boundaries of my knowledge.

Basically, I've got a failing WD Rapter SATA drive on my hands (after an incredibly stable run with Fiesty) - or a severely corrupt ext3 filesystem - I'm not positive which.  SMART analysis suggests the drive is failing.

Luckily, I was able to install a fresh copy of Hardy on a functioning drive - so I've got a clean, stable OS drive to play with my failing drive.

Essentially, I was getting the following errors (sorry, this output is from my notes):

```
EXT3-fs error
device sdb1 ext3_get_inode_loc: unable to read inode block inode=..., block=...

```

and a repeated cycle of:

```
SRST failed (errno=-16)
COMRESET failed (errno=-16)

```

I also received:


```
EXT3-fs corrupt root inode, run e2fsck

```


From various threads with similar errors, I guessed (hoped) it may be an issue locating a superblock.  I installed TestDisk ([cgsecurity.org/wiki/TestDisk_Download]("http://cgsecurity.org/wiki/TestDisk_Download"))
and re-ran fsck with the superblock data return from TestDisk:

(failed disk is NOT mounted when I run fsck - partly b/c it can't be mounted)

```
$sudo /sbin/fsck.ext3 -b 32768 -B 4096 /dev/sdb1
ext3 recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sdb1: recovering journal
/sbin/fsck.ext3: No such device or address while trying to re-open /dev/sdb1
Segmentation Fault
$

```

My entire machine locked up at this point - which is partly why I have not included perfect copy/paste output here.  The desktop is quite unstable with the failed drive in place.


So, I'd obviously like to recover the files on the drive.  Any ideas/general thoughts would be appreciated!  To summarize:

I.  In general, 'sudo lshw' recognizes the disk and it's partitions when I first boot into gnome.  Hence, commands with '/dev/sdb1' agruments are recognized, but typically fail.  

II.  I attempt to mount the drive into /mnt/ and mount hangs at the terminal prompt.  I can't even ^C it.

III.  It's looking like the low-level linux apps are failing on this drive, is my only hope some type of recovery analysis though an app like TestDisk?  If so, any specific suggestions??  Thanks!!

PS - 

I've downloaded the WD "Data Lifeguard Diagnostic for DOS (CD)" - I boot into it and it gets no where because of the SMART errors.

If it helps, it highlights:

```

ID: 5
Name: Re-allocated Sector Count
Value: 70
Thresh:  140
Worst: 70
```


The software does not attempt any recovery, and forces me to reboot at this point.

Is there any hope of recovering the data from the drive?

---

### Post by bapoumba on 2008-06-04
Threads merged.

---

### Post by Sef on 2008-06-04
I would use [Knoppix Live CD]("http://knoppix.com") and with that and a usb key or external hard drive or other storage device and copy the information from your hard drive to your to storage device.  I have used it to obtain information off of hard drives that either would not boot up or were virus infected Windows.

---

### Post by jimv on 2008-06-04
Never used this program before, but it looks like it might help in your situation:

[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

---

### Post by ZAxisMapping on 2008-06-04
Thanks for the replies!  I will try dd-rescue this weekend - I recall TestDisk project mentioning this application.

I'm open to other suggestions as well, but I will give this a shot and report back this weekend.

---

### Post by ZAxisMapping on 2008-06-11
Well, I salvaged ~6 GB out of 150 GB to a local *.iso.  The first 6 GB (ALL data that was written to the iso) was recovered in literally the first minute of ddrescue.  It continued to run for 2 days, recovering nothing more, while the rate continued to decrease to B/s.  

I haven't tried repairing/mounting the iso yet (not even sure how I'd go about it - use e2fsck first, then try and mount?).  What are the chances of having any files recovered?

---

