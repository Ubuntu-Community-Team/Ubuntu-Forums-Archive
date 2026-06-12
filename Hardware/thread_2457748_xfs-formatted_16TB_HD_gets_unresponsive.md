---
title: "xfs-formatted 16TB HD gets unresponsive"
date: 2021-02-08
forum: Hardware
---

### Post by dieter-erich on 2021-02-08
Hi,
   I installed a 16TB HD and formatted it to xfs. I copied a number of files onto it and eventually found old dead links that I deleted. From there on the HD cannot be accessed any more. When issuing e.g. 'ls' it simply does not react. Also the copying process stopped and I cannot get out of the terminal with <ctrl> c even closing it does not help.  I tried to forcefully unmount it with umount -f but no reaction. 

The following commands give me this:
 
sudo umount -f /dev/sdh
umount: /media/user/16TB: target is busy.

ps -ealf|grep /dev/sdh
0 D root     2011531       1  0  80   0 -   945 -      Feb06 ?        00:00:00 xfs_db -x -p xfs_admin -r -c label -r -c uuid /dev/sdh

but killing the process 2011531 does not work.

Can I only power cycle it or is there another way to get it back to life?
Thanks, DE.

---

### Post by bcschmerker on 2021-02-09
**I haven't experience with Silicon Graphics X File System (not to be confused with X Font Server).**  XFS is understood to be poor at single-thread, metadata-intensive workloads, but otherwise good for ext4-compatible applications.  Oracle Incorporated has a [Known Issues page](https://docs.oracle.com/cd/E93554_01/E92390/html/uek4-known-issues-xfs.html) for XFS 3.5.

I used B-Tree File System for /home on the Hot Rod gPC until 15 January 2021, when POST first refused to complete due to the Super-I/O on the GA-MA78GM-S2HP v2.0 no longer recognizing i8042 keyboards; it proved stable.  B-Tree parallels Sun Microsystems ZFS (now optional on ubuntu 18.04-up) in stability goals using block-level checksumming, asynchronous replication (viz., Copy-On-Write), and inline compression; ZFS betters B-Tree as a RAID-native filesystem and volume manager.

---

### Post by dieter-erich on 2021-02-10
Hi  				 				 					 						 	[**[COLOR=#000000]bcschmerker[/COLOR]**]("https://ubuntuforums.org/member.php?u=609186"),
  thank you for the hint! Another idea came to my mind: The HD is connected via a SATA - USB adapter and not all seem to support such big HDs correctly. Maybe this is a reason. I need to look....

---

