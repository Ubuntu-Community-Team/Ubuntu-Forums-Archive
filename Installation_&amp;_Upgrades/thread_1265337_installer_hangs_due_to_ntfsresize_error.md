---
title: "installer hangs due to ntfsresize error"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by someone_else on 2009-09-13
When running the Ubuntu (9.04) installer (from the LiveCD), it gets past step 3, but once the partition manager is started, the installer will just hang. After letting it run for about 20 minutes, I checked the messages log to find this:

Sep 13 13:07:42 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 13 13:07:42 ubuntu ntfsresize: Device name        : /dev/sda1
Sep 13 13:07:42 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 13 13:07:42 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 13 13:07:42 ubuntu ntfsresize: Current volume size: 500103971328 bytes (500104 MB)
Sep 13 13:07:42 ubuntu ntfsresize: Current device size: 500103971840 bytes (500104 MB)
Sep 13 13:07:42 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 25 bad sectors.
Sep 13 13:07:42 ubuntu ntfsresize: ****************************************************************************
Sep 13 13:07:42 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 13 13:07:42 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 13 13:07:42 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 13 13:07:42 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 13 13:07:42 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 13 13:07:42 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 13 13:07:42 ubuntu ntfsresize: ****************************************************************************
Sep 13 13:07:42 ubuntu partman: Error running 'ntfsresize --info'


These errors keep getting repeated every 8 minutes or so, which to me makes it look like it just keeps on trying without giving me any option to skip the damn thing. After all, I don't want to resize any partition, and I don't want to touch the NTFS partitions (the disk is already partitioned with some EXT3 volumes). So is there any way to skip these checks and get on with the installation process?

Before you ask, I've already tried its suggestions to run 'chkdsk /f /r' on Windows (and reboot twice). The Windows checkdisk is not showing any errors, and I believe that there's nothing actually wrong with the disk itself. See, the data on that disk was cloned from a failing one, so it will probably *look* broken (since the original disk was); but the disk this data is currently on is new, and perfectly fine.

So is there any way to install Ubuntu on this machine without removing the 'offending' disk?

---

### Post by ajgreeny on 2009-09-13
Try deleting the existing ext3 partitions on the disk using the live ubuntu CD's gparted.  Also see if you can mount the windows partition(s) and see what is in them without any errors appearing.  I just wonder if there is a problem with the start and end blocks of the partitions on the disk, and if you can boot into windows and quickly resize the windows partition just by a small amount, just to get a new partition, using the windows disk management tools in vista.

---

### Post by Mark Phelps on 2009-09-13
You're either resizing an existing NTFS partition to make room for Ubuntu, or you're installing using Wubi -- either way, you're messing with the NTFS file system.

As has been mentioned here more times that I care to count, your best bet is to use the Vista Disk Management utility to resize the Vista OS, not GParted.

---

### Post by someone_else on 2009-09-13
@ajgreeny: The NTFS partition in question mounts just fine using the Live CD - no errors or problems browsing it. 

I tried installing Fedora 11, and while it initially appeared to show the same symptoms as Ubuntu (it stalled after initializing the partitioner), after about 5 minutes it started working again and I was able to install Fedora. So the Fedora partitioner will ignore the problem after the initial checks - the Ubuntu one does not, and just keeps at it for as long as you let it.

Again, I ran all the disk checks in Windows, and short of resizing that NTFS partition, I don't know what else I could do. And I'd rather not mess with that partition. I would simply install Ubuntu on a different disk, but the Ubuntu installer won't let me (since it never gets as far as the graphical partition manager). Disabling the disk in BIOS doesn't help either - Ubuntu still sees it. And I'd rather not open the case to physically unplug it.

---

### Post by someone_else on 2009-09-14
Would it be possible to somehow disable the problematic HDD in the live Ubuntu session, so that the partition manager will ignore it?

---

