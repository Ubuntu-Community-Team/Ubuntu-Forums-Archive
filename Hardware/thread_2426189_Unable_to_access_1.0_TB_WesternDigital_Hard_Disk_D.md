---
title: "Unable to access 1.0 TB WesternDigital Hard Disk Drive"
date: 2019-09-05
forum: Hardware
---

### Post by thewell2 on 2019-09-05
Well, here is the problem:

Few days ago I decided to use Ubuntu 18.04.03 LTS, intead of my classic Windows 7.
My PC is an intel i5 3rd. gen on a H81M-S2PH Gigabyte board with 8GiB RAM, I use 3 Hard Disks of 1.0 TB each one without any OS, and a 500GiB disk for Windows. When I decided to use Ubuntu, I just repartitioned and formatted the 500GiB totally to use with Ubuntu, it means I don't have a Windows OS to make some practices.

The case explicit is:
My WDC disk appears on **DISKS** Utility, but it shows two partitions, at the start of HardDrive appears 134Mb of free space and at the next 931.4GiB is allocated a "*Microsoft LDM data (System, Legacy BIOS Bootable)*", in the [DISKS utility]("https://launchpad.net/ubuntu/bionic/+source/gnome-disk-utility"), I can see a button to mount the partition in my other two 1.0 TB disks, but in this partition just the "-" and the config button appears.

In my windows environment, that disk contains my personal  documents, I don't tried to reformat or repartition it, 'cause I don't  have any backup of that data.

Some pages in internet gives tools and methodes to correct possibly corruption on the hard disk drive, I tried to list partitions from the [**fdisk**]("http://manpages.ubuntu.com/manpages/bionic/en/man8/fdisk.8.html") utility

```

$ fdisk -l /dev/sdd
Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 877FE66D-12CB-4438-B4C1-3AED17B13E93

Device      Start        End    Sectors   Size Type
/dev/sdd3  262178 1953523711 1953261534 931.4G Microsoft LDM data

Partition 3 does not start on physical sector boundary.

```
```

$ fdisk -l /dev/sdd3
Disk /dev/sdd3: 931.4 GiB, 1000069905408 bytes, 1953261534 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3072 bytes
Disklabel type: dos
Disk identifier: 0x73736572

Device      Boot      Start        End    Sectors   Size Id Type
/dev/sdd3p1      1920221984 3736432267 1816210284   866G unknown
/dev/sdd3p2      1936028192 3889681299 1953653108 931.6G unknown
/dev/sdd3p3               0          0          0     0B  0 Empty
/dev/sdd3p4        27722122   27722568        447 223.5K  0 Empty

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.


```

And previously I used [**parted**]("http://manpages.ubuntu.com/manpages/bionic/man8/parted.8.html") to get some info of my disk:

```
$ parted -l /dev/sdd

Model: ATA WDC WD10EARX-00N (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start  End     Size    File system  Name  Flags
 3      134MB  1000GB  1000GB  ntfs         tb01  hidden, legacy_boot

```

If someone has any idea of how can I solve this, please let me know.
I really need to access my data :(

---

### Post by TheFu on 2019-09-05
Here's my research, in order, after reading the post ... 

Well, if the other disks weren't properly closed by Windows, then it is likely Windows left them open, so Linux won't touch them.
 Win7 did NOT have that enabled by default like Win8 and later all do.  I don't know if Win7 supported *Fast Start* or not.

If Windows wasn't using a "BASIC Partition", Linux won't have an easy time reading it.
/dev/sdd3 doesn't seem like any device name I've ever seen, so I'm guessing there is some funky Windows non-standard file system happening.  It would be best if you could find a Windows machine and convert to basic partitions and normal NTFS. Then Linux shouldn't have issues accessing the data.

Google says these are "Microsoft Windows dynamic disks". Ouch.  [https://askubuntu.com/questions/1056770/how-can-i-handle-microsoft-ldm-data](https://askubuntu.com/questions/1056770/how-can-i-handle-microsoft-ldm-data) didn't seem like they had much luck.  
[https://ubuntuforums.org/showthread.php?t=2325331](https://ubuntuforums.org/showthread.php?t=2325331) is from 2016, which seems like it magically started working after loading and running 1 package.

---

### Post by oldfred on 2019-09-05
I have seen a user use testdisk to convert MBR dynamic partitions back to basic, if only 4 partitions. With gpt that may not be an absolute requirement.

Only if you have good backups of all the NTFS data inside the dynamic partitions, you can try testdisk.

       Other options also Aomei or even testdisk if only 4 dynamic partitions:
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

It used to be that Linux would not see dynamic partitions at all. But now you maybe can, but grub will not install with other partitions as dynamic.

 From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
    
        Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk if less than 4 dynamic partitions
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418) 
   Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

General rule is to use Windows tools for Windows. 
Most of the Windows third party tools, may only run conversion if you upgrade to a paid version.
If you have good backups you can experiment with Linux tools to try conversion.

Also best not to have NTFS if not using Windows. NTFS need chkdsk & defrag periodically and you cannot do those from Linux. If you have NTFS at least keep a Windows repair flash drive.

---

