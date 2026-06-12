---
title: "External HDD mount problem - Corrupted NTFS sectors"
date: 2014-05-24
forum: Hardware
---

### Post by al1x on 2014-05-24
Hello, my problem is that suddenly I can't mount my external hdd drive. Maybe it was because I removed usb cable accidentally before transmission torrent client finished it's job... Anyway, I've tried to fix the bad sectors with ```
sudo ntfsfix /dev/sdb1
``` but I had no luck... it prompted me to run chkdsk /f because the drive is corrupted. Fortunately I have dual boot system so I booted with command-prompt in safe mode to execute chkdsk /f but it also failed giving me the message "Cannot access volume". Finally, I used gparted to fix bad sectors but it failed too... This is the gparted message generated: [HTML]GParted 0.11.0 --enable-libparted-dmraid[COLOR=#000000][FONT=Times New Roman]Libparted 2.3[/FONT][/COLOR]
Check and repair file system (ntfs) on /dev/sdb1  00:02:54    ( ERROR )    calibrate /dev/sdb1  00:00:00    ( SUCCESS )    path: /dev/sdb1
start: 2,048
end: 976,707,583
size: 976,705,536 (465.73 GiB)check file system on /dev/sdb1 for errors and (if possible) fix them  00:02:54    ( ERROR )    ntfsresize -P -i -f -v /dev/sdb1    ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 500073230848 bytes (500074 MB)
Current device size: 500073234432 bytes (500074 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 16451865 (0xfb0919): extra cluster in $Bitmap
Cluster accounting failed at 16451866 (0xfb091a): extra cluster in $Bitmap
.
.< same messages continue for several lines>
.
.
ERROR(5): Couldn't get $Bitmap $DATA: Input/output error[/HTML]

I have run out of ideas trying to fix the drive and not just format it...
 I will appreciate any help. 
Thanks in advance.

---

### Post by al1x on 2014-05-26
Really, 130 views and nobody has nothing to propose?

---

### Post by Mark Phelps on 2014-05-26
Using ntfsfix is a waste of your time.  At best, it only addresses the most trivial of NTFS errors, and is NOT a substitute for Windows Checkdisk.

What MIGHT work is doing the following:
1) Download and burn a CD of the Minitool Partition Wizard Boot CD (Windows partitioning tool)
2) Boot from the CD
3) Use the option to Check the partition.

If it's a filesystem problem, that is likely to correct the filesystem so you can mount it again.

But, if sectors are actually corrupted, any data previously present in those sectors is gone.

---

### Post by al1x on 2014-05-28
Thanks for the answer but I finally recovered my data using testdisk (after all my efforts to fix the boot sector of the disk using testdisk failed too). I copied them to another external hdd and formatted the corrupted one using gparted.

---

