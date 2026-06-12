---
title: "Trying to use Ubuntu to save my family photos..."
date: 2009-01-11
forum: Hardware
---

### Post by imazman on 2009-01-11
I'm not really sure if this is the ideal site for this posting but I'm hoping someone can help me since I am trying to use Ubuntu on a laptop to save my photos.  And I will rebuild my server using Ubuntu!
If your advice saves my photos, I will gladly make a donation to your favorite fund!  Here's my problem...

I had a home server running Mandrake 10 as the OS for many years.  Recently it wasn't running and it wouldn't boot.  It was configured with two HDDs and both seem to be troubled (possible sabatage?).  The primary drive only held the OS and the secondary drive was for file storage. The server was always on and was used to stream music to my stereo, photos to my tv, host my web site, and my email server...so it was exposed (to some degree) to the Internet.   The OS is on a Western Digital Caviar 22500 (2.6 GB) and the file storage drive is a Western Digital Caviar WD400 (40GB).

FILE SERVER DRIVE (secondary drive):
Has my family photos, music. Music has been re-ripped...but we miss our photos!!!!
I put the HDD in an external drive and plugged it into my laptop running Ubuntu.  This drive takes a little longer for the red light on the external case to turn blue (don't know if that means anything).
Nothing mounts, but an extra entry appears in the /proc/diskstats file.  An excerpt from the /proc/diskstats file is shown below:

   8   16 sdb 19 6 200 552 0 0 0 0 0 552 552

I don't know what all the numbers mean but I believe there should be a follow on line with sdb1 (as you will see further down in my OS drive troubleshooting). I believe this drive had just one partition that was vfat since I used it for file storage and sharing between my wife's Windoze laptop, my x-Windoze laptop (now Ubuntu), and the server itself (Mandrake 10).  I could look at the fstab file from the server to determine the partitions, but the OS partition on the OS drive is bad too.

Running fsck and e2fschk produced the following:

root@gateway1-laptop:~# fsck /dev/sdb
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

root@gateway1-laptop:~# e2fsck -b 8193 /dev/sdb
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

Neither of these were of any help!  Is there something else someone can suggest? If I have to I will spend top dollar to send this out to a professional service but I figured I could try a few simple tests first.

OS DRIVE:
  I believe Mandrake 10 used a journaling or reiser file system but don't remember.  In the external case connected to my linux laptop, it mounted one partition and gave an error it  couldn't mount another.  The partition that mounted was my /home so I could retrieve that data.  I looked in /proc and viewed the file /proc/diskstats, below is an excerpt from the file:

root@gateway1-laptop:less /proc/diskstats
 ... 
   8   16 sdb 193 1145 2823 4192 21 10 248 344 0 2116 4536
   8   17 sdb1 41 420 979 1140 0 0 0 0 0 840 1140
   8   18 sdb2 11 0 46 640 0 0 0 0 0 628 640
   8   21 sdb5 38 404 442 728 0 0 0 0 0 500 728
   8   22 sdb6 86 285 932 1300 21 10 248 344 0 1264 1644

I don't know what all the numbers are but it does jog my memory that the HDD was partitioned something like:
  Partition - Small boot partition (vfat) 
  Partition - /
  Partition - swap
  Partition - home

I ran fschk on sdb2 (assuming it is the root partition):

  > root@gateway1-laptop:~# fsck /dev/sdb2
  > fsck 1.41.3 (12-Oct-2008)
  > e2fsck 1.41.3 (12-Oct-2008)
  > fsck.ext2: Attempt to read block from filesystem resulted in
  > short read while trying to open /dev/sdb2
  > Could this be a zero-length partition?

This didn't help me much so I tried running e2fsck:

  > root@gateway1-laptop:~# e2fsck -b 8193 /dev/sdb2
  > e2fsck 1.41.3 (12-Oct-2008)
  > e2fsck: Invalid argument while trying to open /dev/sdb2
  >
  > The superblock could not be read or does not describe a correct ext2
  > filesystem.  If the device is valid and it really contains an ext2
  > filesystem (and not swap or ufs or something else), then the
  > superblock is corrupt, and you might try running e2fsck with an
  > alternate superblock:
  >     e2fsck -b 8193 <device>

Again this doesn't mean a whole lot to me. Is there something else I can try?  

All help greatly appreciated,
imazman

---

### Post by lloyd_b on 2009-01-11
I don't know how to read the info from "/proc/diskstats" either - could you post the results of the following?
```
fdisk -l /dev/sdb
```
This should be *much* easier to understand.  Note that this requires you to be running as root.  Otherwise, you need to put a "sudo" in front of the command.

Lloyd B.

---

### Post by imazman on 2009-01-11
Yes, I tried that:
>   fdisk -l /dev/sdb
>   Cannot open /dev/sdb

fdisk won't work because the device isn't identified properly.  I ran dmesg after pluggin in the data drive into an external USB and get lots of messages, here are a few lines of interest (ellipsis means I skipped some lines):
>   ...
>   [22644.317509] scsi 16:0:0:0: Direct-Access     WDC WD40 0BB-00CLB0       0000 PQ: 0 ANSI: 0
>   [22644.334456] sd 16:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
>   [22644.338467] sd 16:0:0:0: [sdb] READ CAPACITY(16) failed
>   [22644.338482] sd 16:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
>   [22644.338495] sd 16:0:0:0: [sdb] Use 0xffffffff as device size
>   [22644.338506] sd 16:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
>   ...
>   [22644.423321] sd 16:0:0:0: [sdb] Add. Sense: Address mark not found for id field
>   [22644.423329] end_request: I/O error, dev sdb, sector 0
>   [22644.423336] __ratelimit: 15 callbacks suppressed
>   [22644.423340] Buffer I/O error on device sdb, logical block 0
>   [22644.461160] sd 16:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
>   [22644.461174] sd 16:0:0:0: [sdb] Sense Key : Medium Error [current] 
> ...
>   [22644.799424] end_request: I/O error, dev sdb, sector 0
>   [22644.799454]  unable to read partition table
>   [22644.799685] sd 16:0:0:0: [sdb] Attached SCSI disk
> ...

I'm still trying to figure out what some mean, but two things seem apparent to me:

1) The sixth line has the wrong size of the drive, the drive is a 40GB or 40000MB drive but dmesg is saying it is 2199023 MB or 2199GB!  However, looking at the /proc/partitions file it shows:
>   zman@gateway1-laptop:~$ less /proc/partitions
>   major minor  #blocks  name
>
>      8     0   58605120 sda
>      8     1   57103011 sda1
>      8     2          1 sda2
>      8     5    1502046 sda5
>      8    16 2147483648 sdb

The last entry is exactly half of what dmesg say for the number of blocks, but I don't know what this really concludes.

2) It says it can't read the partition table.

Again I don't know what this really concludes.  ANY help or direction would be beneficial.

Tx,
imazman

---

### Post by imazman on 2009-01-11
Ok, found an inconsistent behavior.  I need to turn on the external drive case and let the drive light turn from red to blue BEFORE plugging in it's usb cable into the Ubuntu laptop.  Otherwise, the usb device is never recognized.
So with that in mind I reran fdisk -l /dev/sdb
The command produced no output and no errors...it just return.  So I'm hunching it did not find a partition table.  Could my hunch be correct?  Is there another test I could perform?  What else can be done?

Tx,
imazman

---

### Post by imazman on 2009-01-11
Ok, found an inconsistent behavior.  I need to turn on the external drive case and let the drive light turn from red to blue BEFORE plugging in it's usb cable into the Ubuntu laptop.  Otherwise, the usb device is never recognized.
So with that in mind I reran fdisk -l /dev/sdb
The command produced no output and no errors...it just return.  So I'm hunching it did not find a partition table.  Could my hunch be correct?  Is there another test I could perform?  What else can be done?

Tx,
imazman

---

