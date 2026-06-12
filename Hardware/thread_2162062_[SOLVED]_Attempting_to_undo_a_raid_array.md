---
title: "[SOLVED] Attempting to undo a raid array"
date: 2013-07-12
forum: Hardware
---

### Post by RJ2312 on 2013-07-12
Hi I hope I am posting in the correct part of the forum. If not please forgive me!  I am new to this forum.  I have limited experience with Linux, also. 

I am attempting to separate a mirrored array that was a take out of a Windows machine.  It was formatted NTFS.  I deleted all the partitions using **Gparted liveCD** and attempted to reformat them as EXT4, but Gparted returned an error that it was unable to format the partitions they were in use.  This was not true since I was running a LiveCD and the disks were not mounted.  I found a thread on your forum titled "H**ow to Break a RAID Configuration non-Destructively**" and was attempting to zero out the superblocks thinking that must be the problem. But, when I tried **sudo mdadm --zero-superblock /dev/sdb**1 I got an error "**unable to open /dev/sdb1 not zeroed**."  I googled this error and the only thing I could find was a question about not being root.  So I tried again, this time I did **sudo su** and then **dadm --zero-superblock /dev/sdb**1, but got the same error.  Any ideas?  :confused:

---

### Post by SaturnusDJ on 2013-07-13
Are you sure the disks are not mounted?
Post
```
mount
```

I think zeroing the superblock only works for mdadm based arrays.

---

### Post by RJ2312 on 2013-07-13
Since I booted from **Gparted liveCD** and as Gparted purpose is to manipulate hard drives I assumed that the hard disks would not be mounted. Also, I attempted to mount and umount them just to be sure.  The result was a complaint by Gparted that "**/dev/sdb" cannot be found in /etc/fstab or /etc/mtab**."

You are probably right with regards to the use of **mdadm**, I am not very knowledgable about RAID arrays. When I started this I had been led to believe that the disks were a takeout of a hardware based RAID system and I assumed that there would be no issues with reformatting the hard disks and putting Ubuntu on them.

---

### Post by steeldriver on 2013-07-13
If it was a motherboard-based 'fakeraid' then the correct tool to remove the superblocks is probably dmraid rather then mdadm - something like

```
sudo dmraid -E /dev/sdb1
```

(assuming sdb1 is a RAIDed **partition** - may be just /dev/sdb if the whole **device** was part of an array). If it was a Windows software RAID then I don't know.

BTW you are not expecting to recover any data from these drives, right?

---

### Post by RJ2312 on 2013-07-15
No I am not hoping to recover data. I purposely deleted the partitions because I was trying to eliminate the data on the drives.  You are probably right regarding the system being software RAID. I had been led to believe it was hardware based, but now believe that it was not.  At any rate the issue has be resolved.  What ever the issue was was obviously memory resident. I tried rebooting, but the problem persisted, but after shutting down over night the problem disappeared when I stated the computer the next morning.  


Thanks to all for your help!

[SOLVED]

---

