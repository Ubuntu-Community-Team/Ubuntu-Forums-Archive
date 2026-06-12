---
title: "Issue with Kingston USB Stick"
date: 2014-04-23
forum: Hardware
---

### Post by Wes_Neary on 2014-04-23
Hello all,

Im a fairly new linux user and am loving it so far, however i have come across an issue with a KIngson Traveller USB Drive.  When inserted the drive doesnt appear, following some consultation form Mr Google i have tried some troubleshooting and get the following results:

it@it:~$ sudo lsusb
Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f3:0046 Elan Microelectronics Corp. 
Bus 001 Device 003: ID 2232:1045  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 03f0:b707 Hewlett-Packard 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
[COLOR=#ff0000]Bus 003 Device 006: ID 0951:1665 Kingston Technology - This is the device i am trying to use[/COLOR]
Bus 003 Device 002: ID 045e:0773 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

it@it:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
256 heads, 63 sectors/track, 15505 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e83914a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 16.1 GB, 16080961536 bytes
255 heads, 63 sectors/track, 1955 cylinders, total 31408128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

[COLOR=#ff0000]
The Device is not listed[/COLOR]

when i look at syslog i see thsi when disk inserted

it@it:~$ sudo tail /var/log/syslog 
Apr 23 09:14:49 it kernel: [  818.568531] sd 10:0:0:0: [sdd] Mode Sense: 45 00 00 00
Apr 23 09:14:49 it kernel: [  818.568813] sd 10:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 23 09:14:49 it kernel: [  818.576512] sd 10:0:0:0: [sdd] READ CAPACITY failed
Apr 23 09:14:49 it kernel: [  818.576517] sd 10:0:0:0: [sdd]  
Apr 23 09:14:49 it kernel: [  818.576519] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 23 09:14:49 it kernel: [  818.576522] sd 10:0:0:0: [sdd]  
Apr 23 09:14:49 it kernel: [  818.576523] Sense Key : Unit Attention [current] 
Apr 23 09:14:49 it kernel: [  818.576527] sd 10:0:0:0: [sdd]  
Apr 23 09:14:49 it kernel: [  818.576530] Add. Sense: Not ready to ready change, medium may have changed
Apr 23 09:14:49 it kernel: [  818.577290] sd 10:0:0:0: [sdd] Attached SCSI removable disk


Hopefully someone will be able to help with this thanks in advance

---

### Post by varunendra on 2014-04-23
Welcome to Ubuntu Forums Wes_Neary !

Does this system have a Gigabyte motherboard? Whether or not, see if there is a feature called "IOMMU" in the BIOS. If there is, try enabling it there, then retry the usb stick.

By the way, what is that 16GB drive in your 'fdisk' output?

Instead of fdisk, please post back the outputs of -
```
sudo blkid
sudo parted -l
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Wes_Neary on 2014-04-23
Hi Varun i am not sure on motherboard its a samsung laptop the 16 gb stick is anothe rusb drive that was running the distro

---

### Post by Wes_Neary on 2014-04-23
I thought it may help if i tried in a different vm see below the output

```
wes@LINSRV01-VM ~ $ sudo blkid
/dev/sda1: UUID="73c26f20-c04b-4fba-b35e-31fda86034c5" TYPE="ext4" 
/dev/sda5: UUID="2c869809-fa60-4d67-8610-0d6d89e6f8cc" TYPE="swap" 
wes@LINSRV01-VM ~ $ sudo parted -l
Model: VMware Virtual disk (scsi)
Disk /dev/sda: 107GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  98.8GB  98.8GB  primary   ext4            boot
 2      98.8GB  107GB   8587MB  extended
 5      98.8GB  107GB   8587MB  logical   linux-swap(v1)




wes@LINSRV01-VM ~ $ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0951:1665 Kingston Technology 
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 004: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 001 Device 002: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

