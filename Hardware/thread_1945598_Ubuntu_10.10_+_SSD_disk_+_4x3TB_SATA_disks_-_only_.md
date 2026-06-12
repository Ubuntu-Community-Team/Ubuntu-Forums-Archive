---
title: "Ubuntu 10.10 + SSD disk + 4x3TB SATA disks - only reading 2.2 TB"
date: 2012-03-23
forum: Hardware
---

### Post by pizzahjul on 2012-03-23
I am trying to set up a system consisting of 1x256GB Samsung ATA SSD drive + 4x3TB Seagate Barracuda S-ATA3 drives in RAID0. The SSD drive is used for the OS, while the Seagate drives shall only be used for storage. 

The problem is that the 3TB drives only shows a 2.2TB capacity. As far as I understand this is normal as long as the partition table is MBR, so I have tried to change it to GPT. That is: I installed Ubuntu 10.04 on the SSD disk - and when finished i used gparted to create GPT partition tables in the 4 3TB disks. I rebooted the computer, but still the 3TB drives shows a capacity of 2.2TB. 

```
~$ sudo fdisk -l /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2199.0 GB, 2199023254528 bytes
256 heads, 63 sectors/track, 266305 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483646+  ee  GPT

```I know fdisk can't be used for GPT, but still it should have reported the 3TB size of the drives?

Furthermore I tried reinstalling the system, with GPT on the SSD drive as well, but still the 3TB drives only shows as 2.2TB.

By the way: I am booting with BIOS - UEFI is not available on my system (which probably would have solved the issue?).

Does anyone have any idea how I proceed to be able to use the whole 3TB of the drives?


PS! I haven't started on the RAID-configuration of the drives. I figured out it would be better if it is possible to read the correct size of the disks first... Nevertheless, any tips and tricks for performing this configuration would be highly appreciated:p

---

### Post by oldfred on 2012-03-23
I do not know RAID so I cannot help on that.

Post this and download gdisk if you have not. Change drive to sdb or whatever yours is.

sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

gdisk is in the repositories, but you should download the newest version.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by pizzahjul on 2012-04-30
First of all - I apologize for leaving my own forum thread, but now I am back trying to figure out this issue. I have run the commands suggested by you, oldfred, and here is the output:

```
~$ sudo parted /dev/sdb unit s print
Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sdb: 4294967294s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

``````
~$ sudo sfdisk -l -uS

Disk /dev/sda: 31130 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 298797055  298795008  83  Linux
/dev/sda2     298799102 500117503  201318402   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     298799104 500117503  201318400  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 267349 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1             1 4294967293 4294967293  ee  GPT
        start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
``````
~$ sudo gdisk -l /dev/sdb 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 4294967294 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 55CE6B35-49AD-4337-95FB-0579C557CF20
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967260
Partitions will be aligned on 2048-sector boundaries
Total free space is 4294967227 sectors (2.0 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
```

---

### Post by oldfred on 2012-04-30
I do use gpt with BIOS, but have to have a small 1MB bios_grub partition for grub2 to install correctly.

I have only used gpt on my 160GB drive and a 16GB flash to learn about gpt, and now on my 60GB SSD. So I do not know all the issues with very large drives. It does not look like any of the tools see the 3GB size. I wonder if using MBR set the protective MBR table to the maximum value of 2.2TB and now everything is reading that.

Can you erase/update the protective MBR and totally reformat. I have only used gparted. 

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
GPT fdisk Tutorial 
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by pizzahjul on 2012-05-03
I have now discovered that the disks behave differently depending on  which port on the motherboard I connect to. The computer in question is a  Dell Precision T7500 Westmere with Intel 5520 chipset and an integrated  LSI 1068e SAS/SATA 3.0Gb/s controller. The card has three SATA-ports +  four HDD-ports. When connecting the 3TB Seagate Barracuda (ST3000DM001)  disk to an HDD port - only 2TB capacity seems available. However, when  connecting one of the disks to the SATA port, the full capacity is  available.

I have therefore connected the Seagate disks one-by-one to the SATA-port, booted the disk using a live USB disk with PartedMagic, formatted the disk with GPT and ext4 file system. This seemed to work fine for each of the four 3TB disks, and I therefore put them back in the original set-up: the SSD-disk connected to SATA and the four 3TB disks connected to each of the four HDD-ports. I restarted the system and find the following:

```
$ sudo parted /dev/sdb unit s print
Error: Invalid argument during seek for read on /dev/sdb                  
Retry/Ignore/Cancel? I                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? OK                                                             
Backtrace has 8 calls on stack:
  8: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x2e) [0x7f31bb6e52ee]
  7: /lib/x86_64-linux-gnu/libparted.so.0(+0x4080c) [0x7f31bb71680c]
  6: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x58) [0x7f31bb6eb4d8]
  5: parted() [0x406cb1]
  4: parted(non_interactive_mode+0x8c) [0x40da4c]
  3: parted(main+0x1407) [0x406387]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f31baed176d]
  1: parted() [0x406451]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:980 in function
_parse_header() failed.
``````
$ sudo sfdisk -l -uS

Disk /dev/sda: 31130 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 298797055  298795008  83  Linux
/dev/sda2     298799102 500117503  201318402   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     298799104 500117503  201318400  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.
```
```
$ sudo gdisk -l /dev/sdb 
GPT fdisk (gdisk) version 0.8.1

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdb: 4294967294 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 873EB9BD-CD27-4861-956E-12B6582A5D91
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860532223   2.7 TiB     0700  

```

Does anyone have an idea what causes this? Can the problem be connected to the controller on the motherboard?

---

### Post by oldfred on 2012-05-03
Are not the HDD ports SATA ports?

I know my BIOS on Gigabyte board has different settings for IDE channels 0/1 and 2/3 but has 6 SATA ports. But I have turned on AHCI and it only uses that.

What BIOS settings do you have?

---

### Post by pizzahjul on 2012-05-04
I am not sure if the HDD ports are SATA or not, but I have been told by Dell that they do not support disks larger than 2TB! Dell claims that this mother board and the corresponding disk controller does not support disks above 2TB :-(
 
I therefore have the following options left:
1) change the 3TB disks to 2TB disks
2) change computer
3) find a disk controller which supports four 3TB SATA disks
 
Option 1 and 2 is not where I want to go. The question is then: is it possible to find an external disk controller with 3TB SATA disk support, which is compatible with the rest of the system as well as ubuntu?
 
Anyone have any good suggestions?

---

### Post by pizzahjul on 2012-06-06
Finally I managed to solve the problem. As mentioned in the previous post, I found that the problem was not connected to the software, but rather the mother board and the disk controller. When ordering the computer from Dell I specified that I wanted to use as large hard drives as possible. Dell replied that they couldn't deliver large hard drives at that time due to the situation in Thailand. Hence, I ordered the hard drives elsewhere. However, Dell "forgot" to mention that the hardware only supports hard drives up to 2TB...
 
The solution was therefore to find a disk controller which could be installed in one of the PCI slots. I ended up with a RAID-controller card from Adaptec: Adaptec RAID 6405. This card supports large hard drives with transfer rates of 6 Gb/s. Furthermore, Adaptec has created drivers for Ubuntu (and many other OS-es). Actually, the driver is included in the kernel since kernel 2.6.39 :). Since I started this forum thread I have changed from Ubuntu 10.10 to 12.04, where the driver is included.
 
This card also supports several RAID setups. It was very easy to set up the RAID0 configuration I desired - now giving me a total of 11TB available as "one" disk :-)

---

### Post by WTF_Shelley on 2012-06-06
not trolling but with 4 drives why not raid 5, nearly as fast safer and you get much more storage from the drives raid 5 n-1 raid 0 n/2

---

