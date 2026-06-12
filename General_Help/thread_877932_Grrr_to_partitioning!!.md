---
title: "Grrr to partitioning!!"
date: 2008-08-02
forum: General Help
---

### Post by earthmeLon on 2008-08-02
I was running Ubuntu by itself on my PC for a while.  I had a couple of HDD's with NTFS partitions on them and everything was working beautifully.  I got a new computer for Ubuntu, and installed Vista on the old box.

Now whenever I boot Windows, I only have access to 3/5 HDD's.  One of the ones I cannot access is listed under Computer, but when I try to access it, it says:

```

F:\ is not accessible
The file or directory is corrupted and unreadable.

```

Looking at Computer Management>Disk Management under Admin Tools, I see my other HDD's/partitions, but they are listed just as Healthy (Primary Partition)'s, with no File System type.  The F:\ is listed as RAW.


In writting this, I already understand that Windows doesnt read ext3/rieserfs/etc. I need to figure out how to get Windows to correctly identify/read my NTFS partitions.

Any suggestions?
Thanks in advance :D

---

### Post by sayakb on 2008-08-02
Install EXT2 IFS driver in Windows to read/write ext2/ext3 in Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)
Also, run a scandisk by doing:
```
chkdsk /f f:
```in **cmd** in Windows to correct NTFS filesystem errors and try accessing them again.

---

### Post by geirha on 2008-08-02
Could you post the output of ```
sudo fdisk -l
``` from a terminal in Ubuntu, and identify the partition in question from that list?

And if you can get a similar list from windows, that would be helpful too. (Don't know how to get such a list in Windows myself though)

---

### Post by earthmeLon on 2008-08-02
> **LinuxIsInnovation said:**
> 
Also, run a scandisk by doing:
```
chkdsk /f f:
```in **cmd** in Windows to correct NTFS filesystem errors and try accessing them again.

Thanks for the suggestion.  

```

The type of the file system is NTFS.
Volume label is Boomer.

CHKDSK is verifying files (stage 1 of 3)...
  56361 file records processed.
File verification completed.
  2350 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  65137 index entries processed.
Index verification completed.
  0 unindexed files processed.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  56361 security descriptors processed.
Security descriptor verification completed.
  4388 data files processed.
Windows has checked the file system and found no problems.

 488375968 KB total disk space.
 393784556 KB in 34846 files.
     27576 KB in 4390 indexes.
         0 KB in bad sectors.
    142536 KB in use by the system.
     65536 KB occupied by the log file.
  94421300 KB available on disk.

      4096 bytes in each allocation unit.
 122093992 total allocation units on disk.
  23605325 allocation units available on disk.

```

The partitions is still showing up as RAW, though, and is not accessible.  I will post a list of what Windows shows vs Ubuntu shortly.

---

### Post by earthmeLon on 2008-08-04
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9c5a9c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244194304    7  HPFS/NTFS
/dev/sda2           30402       30662     2096482+  82  Linux swap / Solaris
/dev/sda3           30663       34487    30724312+  83  Linux
/dev/sda4           34488       60801   211367205   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4becfd13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca22a8d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2       60801   488376000    5  Extended
/dev/sdc5               2       60801   488375968+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000d02

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdd1               1       60801   488384001    7  HPFS/NTFS**

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       13055   104857600+  83  Linux
/dev/sde2           13056       60801   383519745   83  Linux


The bold is the HDD that will show up under Windows, but Windows cannot read it.

SDA1 = Windows (Works fine)
SDA2-4 = Reserved for Linux (Works fine)
SDB1 = Windows (Works fine)
SDC5 = Windows (Broken) (chkdsk runs, but fixes nothing)
SDD1 = Windows (Works fine)
SDE1 = Windows (Doesnt work, but I realize it's ext3, so I can fix that :D)

---

### Post by earthmeLon on 2008-08-04
I booted into Gparted boot disc and my SDE1 is now showing up as NTFS (like I thought it was) but it also cannot be read by windows.

The weird thing is that SDC5 (the other broken partition) shows up under windows, I just can't access the drive.  With the SDE1, it isn't even showing up.

le sigh v_v

---

### Post by earthmeLon on 2008-08-05
Okay, I've used chkdsk /f F: 1000 times.  Every time it realizes the partition is NTFS, but doesnt do anything about it.  I tried running TestDisk (Under Windows) and tried to fix the BS and the MFT (whatever the hell that means) but it still isnt working (after a reboot).  The funny thing is, TestDisk and Ubuntu can both read the files from the partition.

Im so confused >_<


```

Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS              1   1  1 60800 254 63  976751937 [Boomer]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

---

### Post by jimv on 2008-08-05
It might be easiest just to copy the data on that drive to another with Ubuntu, and then format the drive again.

---

### Post by earthmeLon on 2008-08-05
Yeah.  It'll take 5 hours to do that, which is a lot shorter than the time I've spent trying to fix this.  That isn't a real solution for me, though.  I want to know what went wrong, how to fix it, and how to keep it from happening again.

---

### Post by earthmeLon on 2008-08-05
Hmmm.

This drive is the only Logical partition.  I realized that Windows won't read a logical partition, unless there is a primary one on the same hdd (?). So, with the extra 7mb left on the HDD, i created a primary linux swap (because I dont want that partition to show up on windows).

I have to go to bed, so I will try again tomorrow.  Does anybody know if this might work if I use another type of primary partition with it?

Is there a way to convert a logical partition into a primary without moving data all over the place?

Thanks again.  If I dont get an answer by tomorrow I guess I'm buying a new HDD, giving in, and doing what jimv suggested....

---

### Post by jimv on 2008-08-05
Ok, I have an idea before you give in.

Installed testdesk in Ubuntu: sudo apt-get install testdisk
Run testdisk: sudo testdesk
Select the trouble drive.
Select Intel
Select Advanced
Highlight the partition, and at the bottom, select Boot
Select Rebuild BS
Choose Write

When it's done, boot back into Windows and try the drive.

EDIT:

If that doesn't work, try running "fixboot f:" from the recovery console on the Vista disk.

---

### Post by earthmeLon on 2008-08-05
Tried all of that.  Nothing worked.  

Thanks for everybody's help, I'm off to transfer some data!!!

---

