---
title: "Hard Drive no Longer Visible"
date: 2011-02-10
forum: Hardware
---

### Post by smacream on 2011-02-10
Hi,


I have desktop running Ubunt 9.10 (Karmic) with 3 SATA hard drives. The first (bootable) has 500GB, and 2 more Western Digital 2TB drives I had installed about a year ago. All seemed ok until, I got a S.M.A.R.T error during POST stage of boot. It said that  "Status Bad, Backup and Replace" for one of the 2TB drives. When I logged in to Ubuntu this hadn't mounted whereas the others had. I was able to mount it using "mount -a" and start backing up files from bad disk to other 2TB disk. There were some problems with backup with some files failing to copy over.

I shutdown the machine, and later started it up again. Same error from SMART. This time when Ubuntu was loading, lots of messages flashed up on screen. When I logged in, I could not mount the bad drive again. Also when I looked at gparted it did not show it in drop down menu. Nor did it appear when I ran "disk -l". I tried running "lshw -C disk" but this seemed to hang at SCSI stage [eventually had to reboot].  I tried using e2fsck but kept getting this error: 

"Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1. Could this be a zero length partition?"

I tried using parted from command line and got error message Error: /dev/sdb1: unrecognised disk label. (Also tried /dev/sdb and got same message). 

I can see the drive in the boot menu, but can't seem to see it in Ubuntu.

Any suggestions?

It wouldn't be the end of the world if I lost the remaining data but is the drive in anyway redeemable?

Any help appreciated!

Thanks.

---

### Post by Grenage on 2011-02-10
I recommend throwing that drive away and forgetting about it.  From your description, it's a classic case of a drive failing; even if you do manage to repartition and format it, it will never be reliable.

---

### Post by gordintoronto on 2011-02-10
> **Grenage said:**
> I recommend throwing that drive away and forgetting about it.  From your description, it's a classic case of a drive failing; even if you do manage to repartition and format it, it will never be reliable.

+1

If I had an external drive case handy, I might try mounting the drive in it to see if I could recover the remaining data, then I would smash the drive with a hammer.

---

### Post by smacream on 2011-02-15
Ok. Thanks.

---

