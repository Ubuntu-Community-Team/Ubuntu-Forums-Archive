---
title: "hard drive failure after power failure"
date: 2014-11-16
forum: Hardware
---

### Post by rogerdg on 2014-11-16
Hi, I was doing an upgrade to 14.10 yesterday evening.  After the upgrade completed I was attempting to create a video by editing a clip taken with my camera.  While my computer was writing data to the hard disk I experienced a brief power outage.  When the computer attempted to boot I saw an error message stating that there was a problem locating a file on the drive.

I am using a copy of Ubuntu from a memory stick on the failing computer.  Gparted sees the drive (sda) and it's partitions as follows:

/dev/sda1 ext4           size:229.28GiB Used:103.33GiB unused:125.96GiB flags:boot
/dev/sda2 extended   size:    3.60GiB used:           ---   unused:          ---   flags:(none)
/dev/sda5 linux-swap size:    3.60GiB used:192.24MiB unused:    3.41GiB flags:(none)

I suspect that one or more superblocks have been damaged.  I need to know if it is possible to regain access to the data on the drive.  I am aware that I may not be able to recover everything, but I need to try to recover the drive before I give up and attempt to reformat the drive and reinstall Ubuntu.  I love linux because of it's journaling file system, but I don't know how to use that information to make the drive usable again.

Can anyone help me?  I'd hate to lose all 103 Gig of data on the drive.
Thanks,

Roger

---

### Post by weatherman2 on 2014-11-16
OK, have you tried to mount /dev/sda1 using the live Ubuntu session?  What happens when you try?

You can try running e2fsck on /dev/sda1 as well.  That can fix issues in the filesystem.

You should also check the S.M.A.R.T. status of the drive to see if it is experiencing some sort of hardware failure.  You can install GSmartControl in a live session (if asked, skip mail setup) and then check the Attributes of the drive and look for any that are highlighted in pink or red; if none, the drive probably isn't failing.

---

### Post by tgalati4 on 2014-11-16
If you can't *fsck* the drive from a Live session, then you can install *testdisk* and try that to recover the partition and file descripters.  If that doesn't work, then use *photorec* to recover files.

Have some large USB sticks available to receive the data.

Add "Purchase UPS" to your todo list.

---

### Post by rogerdg on 2014-11-16
Attempted to mount /dev/sda1 using 

# mkdir /media/disk
# mount /dev/sda1 /media/disk

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This didn't get me very far...

Following the suggestion:

# dmesg | tail
[ 6133.602162] sd 0:0:0:0: [sda]  
[ 6133.602168] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6133.602174] sd 0:0:0:0: [sda] CDB: 
[ 6133.602178] Read(10): 28 00 0e 46 56 60 00 00 08 00
[ 6133.602196] end_request: I/O error, dev sda, sector 239490660
[ 6133.602245] JBD2: Failed to read block at offset 18892
[ 6133.602249] ata1: EH complete
[ 6133.649353] JBD2: recovery failed
[ 6133.649367] EXT4-fs (sda1): error loading journal
[ 6818.353398] r8712u 1-4:1.0 wlan1: r8712_got_addbareq_event_callback: mac = 4e:f8:b3:84:d5:23, seq = 30336, tid = 0

Doesn't tell me much except that the mount failed, but not how I might resolve the issue.

Trying e2fsck results in a question.  Should I answer yes or no?

# e2fsck /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda1: recovering journal
Error reading block 29936076 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? 

I am going to wait for a suggestion before proceeding, but while I'm waiting I'll try installing GSmartControl (just in case I need it).

GSmartControl fails to install.  

#apt-get install GSmartControl
Package 'gsmartcontrol' has no installation candidate.

---

### Post by rogerdg on 2014-11-16
# apt-get install GSmartControl

Package 'gsmartcontrol' has no installation candidate

This doesn't help much either.... I'll keep waiting.

---

### Post by rogerdg on 2014-11-16
I used Control-C to cancel the e2fsck, and received a message stating that the drive still has some errors.  The amazing thing is that now I can mount the drive and it appears that the data on the drive is intact.

Thanks for the quick replies to my request for help.

I guess I'll have to add "purchase UPS" to my to-do list.

Roger
-- Once again a HAPPY Ubuntu user! :) --

---

### Post by weatherman2 on 2014-11-16
I think you got lucky.  I'd still run GSmartControl on the drive once you get a working Ubuntu up and running.  I'm sure it is possible to install GSmartControl in a live session somehow - but it may be more trouble than its worth.  An alternative is a distro like Parted Magic which has it pre-installed - but there it is called "disk health."  Still a free version of Parted Magic available on Major Geeks I think.  S.M.A.R.T. (which you can access with GSmartControl or "smartctl" in the terminal) is not infallible but it is very useful in checking the status of a hard drive.  

Make sure you get a UPS that has a USB port too, if you want your Ubuntu machine to be able to sense the UPS's battery level - otherwise, once the battery dies (in a prolonged power outage), the power will still go out "unsafely."  Some very cheap UPS units do not have a USB interface so no way for the computer to tell when the UPS battery is about to  go dead.

---

### Post by rogerdg on 2014-11-19
Thanks for all the assistance in recovering my system.  I'm running gsmartcontrol as super-user.  In normal mode it fails to see the smart status of any drives.
I marked the thread solved since my intent was to regain access to the data, and this was successful.

Roger

---

