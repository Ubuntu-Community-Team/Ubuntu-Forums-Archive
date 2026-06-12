---
title: "Eror while resizing internal hard drive."
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by appledoze on 2009-02-16
So I was finally able to resuscitate my Windows, with all my files intact. after running a chkdsk /f I now am given the option to resize /dev/sda1. But whenever I try to, it finds a problem during the run simulation phase. What does this mean? Should I defragment the hard drive more?

Here are details BTW

GParted 0.3.8

Libparted 1.8.9

Shrink /dev/sda1 from 37.26 GiB to 32.13 GiB  00:00:40    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 78140159
size: 78140097 (37.26 GiB)
calculate new size and position of /dev/sda1  00:00:01    ( SUCCESS )
     	
requested start: 63
requested end: 67376609
requested size: 67376547 (32.13 GiB)
new start: 63
new end: 67376609
new size: 67376547 (32.13 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:09    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 40007729664 bytes (40008 MB)
Current device size: 40007729664 bytes (40008 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 33847 MB (84.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 37525 MB 0
Multi-Record : 40008 MB 26898
$MFTMirr : 20004 MB 1
Compressed : 40008 MB 15098
Ordinary : 40008 MB 22699
You might resize at 33846063104 bytes or 33847 MB (freeing 6161 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:00:21    ( ERROR )
     	
run simulation  00:00:21    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 34496792063 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 40007729664 bytes (40008 MB)
Current device size: 40007729664 bytes (40008 MB)
New volume size : 34496786944 bytes (34497 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 33847 MB (84.6%)
Collecting resizing constraints ...
Needed relocations : 1156974 (4739 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1056 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00:09    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 40007729664 bytes (40008 MB)
Current device size: 40007729664 bytes (40008 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 33847 MB (84.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 37525 MB 0
Multi-Record : 40008 MB 26898
$MFTMirr : 20004 MB 1
Compressed : 40008 MB 15098
Ordinary : 40008 MB 22699
You might resize at 33846063104 bytes or 33847 MB (freeing 6161 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00:00    ( SUCCESS )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 40007729664 bytes (40008 MB)
Current device size: 40007729664 bytes (40008 MB)
New volume size : 40007725568 bytes (40008 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 40007729664 bytes (40008 MB)
Current device size: 40007729664 bytes (40008 MB)
New volume size : 40007725568 bytes (40008 MB)
Nothing to do: NTFS volume size is already OK.

---

### Post by AllenGG on 2009-02-16
Dual boot ? 
If so run Windows defrag 1st. Watch in action. you should see a big change in disk use. If not
shrinking with GParted or ? may not work.

---

### Post by appledoze on 2009-02-16
Yeah I'm trying to create a dual boot. Also, if I shrink the drive from the right where there's still free space, will all mu used data still be intact?

---

### Post by AllenGG on 2009-02-16
Normally there are no problems with defrag. But you say fdisk -l shows more space than is true ?

---

### Post by Mark Phelps on 2009-02-17
Didn't notice which MS Windows you're running -- XP or Vista? If XP, try downloading and burning the latest GParted LiveCD.  They've updated the version considerably from the one resident in Ubuntu.  IF Vista, do NOT use GParted or Ubuntu as you will run the risk of corrupting the Vista OS and, unless you have a Vista DVD to repair the boot loader, you will end up with an unbootable Vista OS.

---

### Post by appledoze on 2009-02-17
> **Mark Phelps said:**
> Didn't notice which MS Windows you're running -- XP or Vista? If XP, try downloading and burning the latest GParted LiveCD.  They've updated the version considerably from the one resident in Ubuntu.  IF Vista, do NOT use GParted or Ubuntu as you will run the risk of corrupting the Vista OS and, unless you have a Vista DVD to repair the boot loader, you will end up with an unbootable Vista OS.
I have XP, and I used the Gparted Live CD, but got the same response.

---

### Post by Mark Phelps on 2009-02-18
Well .. if the Linux utilities won't work, your only option would be to try MS Windows utilities such as Acronis Disk Director or Paragon Disk Manager -- but those are all retail products and will cost you $50 or so.  I think both offer trial versions, but I don't know what features they support. Trial versions typically disable the ability to write drive info.

---

