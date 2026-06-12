---
title: "Can't clear the &quot;read only&quot; attribute from a USB stick"
date: 2022-02-26
forum: Hardware
---

### Post by LannaD on 2022-02-26
I've read at least 7 different threads that didn't solve my problem. I'm one more failed solution away from taking a hammer to the USB stick itself and my computer at work.

I bought a Verbatim 128GB Store ‘n’ Go [https://www.verbatim.com/prod/usb-drives/everyday-usb-drives/store-n-go-v3-usb-3.0-drive-sku-49189/](https://www.verbatim.com/prod/usb-drives/everyday-usb-drives/store-n-go-v3-usb-3.0-drive-sku-49189/) and used it for quite a while with no problems.

The trouble started when I tried to back up and migrate the contents of a hard drive from an old PC (32 bit Ubuntu) to a new one (64 bit Ubuntu) and the USB stick has been stuck in read-only mode ever since. Here are some of the things I tried:

Running ```
$ sudo fdisk -l /dev/sdb
``` gives the following results:
```
Disk /dev/sdb: 117,5 GiB, 126149591040 bytes, 246385920 sectors
Disk model: STORE N GO      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x73736572

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1       1920221984 3736432267 1816210284   866G 72 unknown
/dev/sdb2       1936028192 3889681299 1953653108 931,6G 6c unknown
/dev/sdb3                0          0          0     0B  0 Empty
/dev/sdb4         27722122   27722568        447 223,5K  0 Empty

Partition table entries are not in disk order.
```
The sizes clearly don't add up.

Running ```
$ sudo fsck -V /dev/sdb
``` gives this result:
```
fsck from util-linux 2.34
```

Running ```
$ sudo hdparm /dev/sdb
``` gives these results:
```
/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 multcount     =  0 (off)
 readonly      =  1 (on)
 readahead     = 256 (on)
 geometry      = 15336/255/63, sectors = 246385920, start = 0
```

```
$ sudo fdisk /dev/sdb
``` results in an error:
```
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdb: Read-only file system
```

Trying to clear the read-only attribute fails:
```
$ sudo hdparm -r0 /dev/sdb

/dev/sdb:
 setting readonly to 0 (off)
 readonly      =  1 (on)
```

I tried running a check in gparted, but every time try saving the results, the program hangs. I managed to this report out of it:

[HTML]Device:    /dev/sdb
Model:    Verbatim STORE N GO
Serial:    none
Sector size:    512
Total sectors:    246385920
 
Heads:    255
Sectors/track:    2
Cylinders:    483109
 
Partition table:    none
 
Partition    Type    Start    End    Flags    Partition Name    File System    Label    Mount Point
/dev/sdb    Unpartitioned    0    246385919            ntfs    128 Gb[/HTML]

Then this:
[HTML]Check and repair file system (ntfs) on /dev/sdb  00:00:01    ( ERROR )         calibrate /dev/sdb  00:00:00    ( SUCCESS )             path: /dev/sdb (device)
start: 0
end: 246385919
size: 246385920 (117.49 GiB)          check file system on /dev/sdb for errors and (if possible) fix them  00:00:01    ( ERROR )             ntfsresize -i -f -v '/dev/sdb'  00:00:01    ( ERROR )             ntfsresize v2017.3.23AR.3 (libntfs-3g)
Device name        : /dev/sdb
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 126149587456 bytes (126150 MB)
Current device size: 126149591040 bytes (126150 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Cluster accounting failed at 9437184 (0x900000): missing cluster in $Bitmap
...
<There are hundreds of very similar error lines between these two. I left them out for brevity.>
...
Cluster accounting failed at 9666459 (0x937f9b): extra cluster in $Bitmap
Filesystem check failed! Totally 60370 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
[/HTML]

I do have WIndows 10 on a separate SSD, but chkdisk /f also can't get past the read-only attribute.

The data on the USB stick is no longer really needed, so I'd be more than happy to just find a way to erase/format it.

So, is this flash drive ready for a good hammering, or there any hope? Thank you in advance.

Cheers.

---

### Post by yancek on 2022-02-26
You should be able to use GParted to create a partition table which you don't have on the drive since you don't need the data. Creating a partition table will delete all data on the device.  Open GParted and click on the Device tab at the top and you should jave am option to create a partition table.  Since the drive is formatted with a windows ntfs partition, you should be able to do this in windows but I don't inow what tool you would usel

---

### Post by LannaD on 2022-02-26
I tried your suggestion, but attempting to create a new partition table still results in "Can't write to /dev/sdb, because it is opened read-only" error.

---

### Post by tea for one on 2022-02-28
If you have successfully created a partition table, then the device would appear via:-

```
edited@edited:~$ sudo parted -l
[sudo] password for edited: 
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt [COLOR="#0000FF"](or msdos)[/COLOR]
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags
edited@edited:~$ 
```

Partition details are missing because they haven't been created yet.

After creating a partition, this is the result:-
```
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4009MB  4008MB  fat32              msftdata

```
Can you post your output from **sudo parted -l** after creating a partition table (but before creating partitions)?

---

