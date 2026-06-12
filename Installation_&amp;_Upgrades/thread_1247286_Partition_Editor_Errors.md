---
title: "Partition Editor Errors"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by dannymichel on 2009-08-22
does anyone know what this means?
```
GParted 0.4.3

Libparted 1.8.8
Move /dev/sda1 to the left and grow it from 198.79 GiB to 232.88 GiB  02:13:52    ( ERROR )
     	
calibrate /dev/sda1  00:00:01    ( SUCCESS )
     	
path: /dev/sda1
start: 559878144
end: 976764927
size: 416886784 (198.79 GiB)
calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
     	
requested start: 0
requested end: 488392064
requested size: 488392065 (232.88 GiB)
new start: 63
new end: 488392064
new size: 488392002 (232.88 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:07    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213446029824 bytes (213447 MB)
Current device size: 213446033408 bytes (213447 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 175595 MB (82.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 179382 MB 0
Multi-Record : 213446 MB 173896
$MFTMirr : 1 MB 1
Compressed : 213447 MB 184844
Sparse : 199580 MB 57474
Ordinary : 213446 MB 188843
You might resize at 175594074112 bytes or 175595 MB (freeing 37852 MB).
Please make a test run using both the -n and -s options before real resizing!
move partition to the left  00:00:10    ( SUCCESS )
     	
old start: 559878144
old end: 976764927
old size: 416886784 (198.79 GiB)
new start: 63
new end: 416886846
new size: 416886784 (198.79 GiB)
move file system to the left  02:13:24    ( SUCCESS )
     	
using internal algorithm
copy 416886784 sectors
finding optimal blocksize
     	
copy 65536 sectors using a blocksize of 64 sectors  00:00:09    ( SUCCESS )
     	
65536 of 65536 copied
8.72993 seconds
copy 65536 sectors using a blocksize of 128 sectors  00:00:09    ( SUCCESS )
     	
65536 of 65536 copied
8.85296 seconds
copy 65536 sectors using a blocksize of 256 sectors  00:00:07    ( SUCCESS )
     	
65536 of 65536 copied
6.75944 seconds
copy 65536 sectors using a blocksize of 512 sectors  00:00:05    ( SUCCESS )
     	
65536 of 65536 copied
4.96972 seconds
copy 65536 sectors using a blocksize of 1024 sectors  00:00:03    ( SUCCESS )
     	
65536 of 65536 copied
3.09031 seconds
copy 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 copied
2.05489 seconds
copy 65536 sectors using a blocksize of 4096 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.60389 seconds
copy 65536 sectors using a blocksize of 8192 sectors  00:00:02    ( SUCCESS )
     	
65536 of 65536 copied
1.32214 seconds
copy 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.16264 seconds
copy 65536 sectors using a blocksize of 32768 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.08199 seconds
copy 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
     	
65536 of 65536 copied
1.12166 seconds
optimal blocksize is 32768 sectors (16.00 MiB)
copy 416165888 sectors using a blocksize of 32768 sectors  02:12:43    ( SUCCESS )
     	
416165888 of 416165888 copied
416886784 sectors copied
updating boot sector of ntfs file system on /dev/sda1  00:00:02    ( SUCCESS )
     	
echo 3f000000 | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sda1 bs=1 seek=28
     	
4+0 records in
4+0 records out
4 bytes (4 B) copied, 0.282919 s, 0.0 kB/s
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:07    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213446029824 bytes (213447 MB)
Current device size: 213446033408 bytes (213447 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 175595 MB (82.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 179382 MB 0
Multi-Record : 213446 MB 173896
$MFTMirr : 1 MB 1
Compressed : 213447 MB 184844
Sparse : 199580 MB 57474
Ordinary : 213446 MB 188843
You might resize at 175594074112 bytes or 175595 MB (freeing 37852 MB).
Please make a test run using both the -n and -s options before real resizing!
grow file system to fill the partition  00:00:01    ( ERROR )
     	
run simulation  00:00:00    ( SUCCESS )
     	
ntfsresize -P --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 213446029824 bytes (213447 MB)
Current device size: 213446033408 bytes (213447 MB)
New volume size : 213446029824 bytes (213447 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00:01    ( ERROR )
     	
ntfsresize -P --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening &apos;/dev/sda1&apos; as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

========================================

```

---

### Post by drs305 on 2009-08-22
Have you tried doing what the error message states:
> 
Please shutdown Windows properly before using this software! Note, if you have run chkdsk previously then boot Windows again which will automatically initialize the journal correctly.


If windows is not available, you can try ntfsfix, part of the ntfsprogs app.

---

### Post by dannymichel on 2009-08-22
> **drs305 said:**
> Have you tried doing what the error message states:


If windows is not available, you can try ntfsfix, part of the ntfsprogs app.

thanks

---

