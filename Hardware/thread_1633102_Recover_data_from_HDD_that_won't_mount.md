---
title: "Recover data from HDD that won't mount?"
date: 2010-11-28
forum: Hardware
---

### Post by elricscripts on 2010-11-28
My system failed to boot, so I used ubuntu 10.04 live CD to find the problem.  Apparently my main ext4 (/dev/sda1) has five bad sectors.  I can't even mount the thing anymore.

Is there any way to recover a few files from the disk before I toss it?  Running the smart data, I see it has 5 bad sectors.  I receive a warning under "Current Pending Sector Count".

When i try to mount I receive the message:
"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

dmesg | tail has the message:
"[  895.260267] Descriptor sense data with sense descriptors (in hex):
[  895.260272]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  895.260290]         0e 46 fc c8 
[  895.260297] sd 6:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  895.260307] sd 6:0:0:0: [sda] CDB: Read(10): 28 00 0e 46 fc c8 00 01 00 00
[  895.260323] end_request: I/O error, dev sda, sector 239533256
[  895.260363] ata7: EH complete
[  895.260386] JBD: Failed to read block at offset 24217
[  895.260397] JBD: recovery failed
[  895.260401] EXT4-fs (sda1): error loading journal
"

Any ideas would be great... thanks.

---

### Post by akand074 on 2010-11-28
I'm not sure if this will work for you, but when I accidentally formatted my entire hard drive without backing up I used [this]("http://www.cgsecurity.org/wiki/TestDisk") and got everything back. Not sure if it would be helpful in your situation as well, its been a while since I've used it so I forget what options it has. Perhaps other people might have some better suggestions as well.[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by elricscripts on 2010-11-28
Thank you for the quick reply!!!!  Looks like TestDisk may be what i'm looking for.  Going to try it out... *crosses finger*

---

### Post by elricscripts on 2010-11-28
Thank you ... it worked!!!

I was able to restore the superblock with TestDisk
(adv menu / choose partition / superblock)
Then used the superblock info to fsck the disk and have it readable again.

Backing up now.  Hopefully it will copy all the data i need....

Reference for others who may find this thread:
[http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock)

---

### Post by akand074 on 2010-11-29
That is great to hear. So did you end up copying all your data successfully? If so you should mark this thread as "Solved" from the thread tools option in order to help people in the future.

---

