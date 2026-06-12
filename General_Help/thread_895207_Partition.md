---
title: "Partition"
date: 2008-08-20
forum: General Help
---

### Post by AryanAngel on 2008-08-20
I am having trouble creating a partition with any partitioning software. I recently tried using GParted 0.3.5 and I received an error. Here is my log can anybody make anything of it? I'd like to get this to work so I can spend less time on XP!
```
GParted 0.3.5

Libparted 1.7.1

Move /dev/sda1 to the left and shrink it from 232.88 GiB to 166.47 GiB  00:19    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 488375999
size: 488375937 (232.88 GiB)
calculate new size and position of /dev/sda1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 349108514
requested size: 349108515 (166.47 GiB)
new start: 63
new end: 349108514
new size: 349108452 (166.47 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:07    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250048479744 bytes (250049 MB)
Current device size: 250048479744 bytes (250049 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 74086 MB (29.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 63724 MB 0
Multi-Record : 219717 MB 5492
$MFTMirr : 125025 MB 1
Compressed : 219374 MB 2210
Sparse : 218688 MB 183824
Ordinary : 219723 MB 130315
You might resize at 74085818368 bytes or 74086 MB (freeing 175963 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:06    ( ERROR )
     	
run simulation  00:06    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 178743527423 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250048479744 bytes (250049 MB)
Current device size: 250048479744 bytes (250049 MB)
New volume size : 178743521792 bytes (178744 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 74086 MB (29.6%)
Collecting resizing constraints ...
Needed relocations : 623546 (2555 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1072 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:05    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250048479744 bytes (250049 MB)
Current device size: 250048479744 bytes (250049 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 74086 MB (29.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 63724 MB 0
Multi-Record : 219717 MB 5492
$MFTMirr : 125025 MB 1
Compressed : 219374 MB 2210
Sparse : 218688 MB 183824
Ordinary : 219723 MB 130315
You might resize at 74085818368 bytes or 74086 MB (freeing 175963 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:01    ( SUCCES )
     	
run simulation  00:01    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250048479744 bytes (250049 MB)
Current device size: 250048479744 bytes (250049 MB)
New volume size : 250048475648 bytes (250049 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250048479744 bytes (250049 MB)
Current device size: 250048479744 bytes (250049 MB)
New volume size : 250048475648 bytes (250049 MB)
Nothing to do: NTFS volume size is already OK.

========================================

Create Primary Partition #1 (ext3, 66.42 GiB) on /dev/sda

========================================

```

---

