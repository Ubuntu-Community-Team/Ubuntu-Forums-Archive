---
title: "Harddisk problem. What to do?"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by z-vet on 2006-10-13
Hi all.
I have a 160 Gb SATA harddisk - Western Digital WDC WD1600JS-60M - with ReiserFS. Disk is less than one year old and worked just fine. However today i transferred some big (several Gigabytes) amount of data to this disk and system just started to freeze. I tried to kill my filemanager, thinking of it to be a problem, but with no luck. Well, i killed an X session (i start it manually) and found the following in console:
```

ata1: command 0x35 timeout, stat 0x58 host_stat 0x21

```
Wanted to reboot but system was hardlocked and i had to use reset button. Well, started up again and tried reiserfsck on this disk. This is an output of reiserfsck /dev/sda without any arguments:
```
###########
reiserfsck --check started at Fri Oct 13 19:47:48 2006
###########
Replaying journal..
No transactions found
Checking internal tree..

Bad root block 0. (--rebuild-tree did not complete)

Aborted

```
/var/log/messages is full of: 
```
| Oct 13 19:15:36 localhost kernel: [17181653.272000] ReiserFS: sda1: warning: vs-13075: reiserfs_read_locked_inode: dead inode read from disk [15437 21211 0x0 SD]. This is likely to be race with knfsd. Ignore
| Oct 13 19:15:36 localhost kernel: [17181653.288000] ReiserFS: sda1: warning: vs-13075: reiserfs_read_locked_inode: dead inode read from disk [15437 21196 0x0 SD]. This is likely to be race with knfsd. Ignore
| Oct 13 19:15:37 localhost kernel: [17181653.464000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
| Oct 13 19:15:37 localhost kernel: [17181653.464000] ReiserFS: sda1: warning: vs-5150: search_by_key: invalid format found in block 17465337. Fsck?
| Oct 13 19:15:37 localhost kernel: [17181653.464000] ReiserFS: sda1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [15437 19521 0x0 SD]
| Oct 13 19:15:37 localhost kernel: [17181653.588000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
| Oct 13 19:15:37 localhost kernel: [17181653.588000] ReiserFS: sda1: warning: vs-5150: search_by_key: invalid format found in block 17465337. Fsck?
| Oct 13 19:15:37 localhost kernel: [17181653.588000] ReiserFS: sda1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [15437 19478 0x0 SD]
| Oct 13 19:15:37 localhost kernel: [17181653.680000] ReiserFS: sda1: warning: vs-13075: reiserfs_read_locked_inode: dead inode read from disk [15437 21164 0x0 SD]. This is likely to be race with knfsd. Ignore
| Oct 13 19:15:37 localhost kernel: [17181653.684000] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
| Oct 13 19:15:37 localhost kernel: [17181653.684000] ReiserFS: sda1: warning: vs-5150: search_by_key: invalid format found in block 17465337. Fsck?
``` again and again.

I'm confused and don't know what to do. What does it mean? My disk is dying, or maybe it's a motherboard's SATA controller or what? I'm busy backing up all data from this disk but what to do next?

---

### Post by Jason_25 on 2006-10-13
Any reason you are using Reiser instead of EXT3?  Despite the fans of the filesystem, I have seen many people with problems with it on these boards.

---

### Post by z-vet on 2006-10-13
Sorry, i can't give any reason why i use ReiserFS. It's just happened. 
Well, i'm backing up all unsaved data from this disk. But what next?

---

### Post by Jason_25 on 2006-10-13
Personally, I would reformat with ext3 and run a SMART check.  Then if it all checks out, copy your stuff back.

---

### Post by z-vet on 2006-10-13
Thank you for quick replies. That exactly what i wanted to do. One question: how actually i do a SMART check?

---

### Post by z-vet on 2006-10-13
Well, Google was my friend as usual. I reformatted the drive with ext3 and trying some SMART checks on it. Will post results later. Now 'tail -f /var/log/messages' shows me this:
```
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: error=0x04 { DriveStatusError }
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: error=0x04 { DriveStatusError }
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 14 02:25:45 localhost kernel: [17181230.536000] ata2: error=0x04 { DriveStatusError }

```
but [this page](http://www.captain.at/howto-linux-driveready-seekcomplete-error-drivestatuserror.php) says it's nothing serious. However, i don't think i can trust this drive.

---

### Post by z-vet on 2006-10-13
Ok, the result of SMART test is:
```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      8110         -
# 2  Short offline       Completed without error       00%      8108         -

```
It shows no errors. I'm in doubt now.

---

### Post by Jason_25 on 2006-10-16
I was having those errors on a friend's 80 gig maxtor drive.  SMART checked out ok too. I replaced the drive with another one and gave the maxtor back for him to test out.  The drive was originally from a Scientific Atlanta DVR that I've had several fail with bad drives in the past.  Also, every maxtor drive I have ever had but one has failed/given errors.  So if that's what you have, I would give your drive a 90% chance it has a hardware problem.

---

### Post by z-vet on 2006-10-26
I went to the store and they replaced the drive with new one. Now on file transfers to the drive i get:
```
tail -f /var/log/messages
Oct 26 16:20:46 localhost kernel: [17253026.412000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 26 16:20:46 localhost kernel: [17253026.412000] ata2: error=0x84 { DriveStatusError BadCRC }
Oct 26 16:23:47 localhost kernel: [17253206.956000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 26 16:23:47 localhost kernel: [17253206.956000] ata2: error=0x84 { DriveStatusError BadCRC }

```
:-k

---

### Post by Jason_25 on 2006-10-28
Sorry to hear that.  Maybe my friend's drive was ok after all.  I think you may have run into an obscure drive controller driver issue.  Maybe something to do with DMA, really beyond what I know.  Can you change kernels and see if you have the same trouble?

---

### Post by zgornel on 2006-10-29
> **Jason_25 said:**
> Sorry to hear that.  Maybe my friend's drive was ok after all.  I think you may have run into an obscure drive controller driver issue.  Maybe something to do with DMA, really beyond what I know.  Can you change kernels and see if you have the same trouble? I agree. It seems to be kernel related rather than hardware. I remember I had similar problems with a 2.6.9 Kernel and a NForce2 IDE controller.

Ok, I found out this: 
[I]Use multi-mode by default (IDEDISK_MULTI_MODE)

If you get this error, try to say Y here:

hda: set_multmode: status=0x51 { DriveReady SeekComplete Error }
hda: set_multmode: error=0x04 { DriveStatusError }

If in doubt, say N.[/I]
In Device Drivers/ATA-ATAPI support/Use multi-mode by defaut while recompiling the kernel
Hope it helps ;)

---

