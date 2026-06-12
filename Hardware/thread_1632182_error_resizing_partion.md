---
title: "error resizing partion"
date: 2010-11-27
forum: Hardware
---

### Post by kenn_robinson on 2010-11-27
I am trying to close off my partition with windows on it, but when I try  to resize it, it fail. Here is a copy of the report I obtained with my  root account (Please  don't give me a hard time for using the root user account, I am aware of  the risks, and I DO NOT use it for everyday use, only for things that  require it)

GParted 0.6.2

Libparted 2.3
Shrink /dev/sda1 from 26.74 GiB to 16.33 GiB  00:00:15    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 56082914
size: 56082852 (26.74 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 28714418688 bytes (28715 MB)
Current device size: 28714420224 bytes (28715 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 17540 MB (61.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 18290 MB 0
Multi-Record : 28567 MB 351
$MFTMirr : 1061 MB 1
Compressed : 28556 MB 23655
Sparse : 27702 MB 48602
Ordinary : 28715 MB 15521
You might resize at 17539063808 bytes or 17540 MB (freeing 11175 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  00:00:06    ( ERROR )
     	
run simulation  00:00:06    ( ERROR )
     	
ntfsresize -P --force /dev/sda1 -s 17539498495 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 28714418688 bytes (28715 MB)
Current device size: 28714420224 bytes (28715 MB)
New volume size : 17539494400 bytes (17540 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 17540 MB (61.1%)
Collecting resizing constraints ...
Needed relocations : 1239150 (5076 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:04    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 28714418688 bytes (28715 MB)
Current device size: 28714420224 bytes (28715 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 17540 MB (61.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 18290 MB 0
Multi-Record : 28567 MB 351
$MFTMirr : 1061 MB 1
Compressed : 28556 MB 23655
Sparse : 27702 MB 48602
Ordinary : 28715 MB 15521
You might resize at 17539063808 bytes or 17540 MB (freeing 11175 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 28714418688 bytes (28715 MB)
Current device size: 28714420224 bytes (28715 MB)
New volume size : 28714414592 bytes (28715 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 28714418688 bytes (28715 MB)
Current device size: 28714420224 bytes (28715 MB)
New volume size : 28714414592 bytes (28715 MB)
Nothing to do: NTFS volume size is already OK.

======================================…

---

