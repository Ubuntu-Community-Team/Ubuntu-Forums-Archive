---
title: "Is it possible to format a write protected Microsoft USB flash drive?"
date: 2018-03-29
forum: Hardware
---

### Post by MibunoOokami on 2018-03-29
I'm trying to format a 16GB USB install disk that I have been given, it contains Windows 7 or something. I could do with an extra flash drive but I can't get it to format because it is read only. Gparted doesn't want anything to do with it and I've looked at a bunch of things online but no luck. One Youtube video looked promising but the command ```
df -Th
``` doesn't list sdc1. Per the title, is it possible to format this flash drive to make it usable as a storage device?

These are the following commands I have tried.
```
mount /dev/sdc1 /media/usb
Error opening read-only '/dev/sdc1': No such device or address
Failed to mount '/dev/sdc1': No such device or address
Either the device is missing or it's powered down, or you have
SoftRAID hardware and must use an activated, different device under
/dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1) to mount NTFS.
Please see the 'dmraid' documentation for help.

```
```
mount /dev/sdc1 /mnt
mount: /dev/sdc1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try       dmesg | tail or so.


```

```
dmesg | tail
[ 6714.479663] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 01 f5 3c 78 00 00 88 00
[ 6714.479667] print_req_error: I/O error, dev sdc, sector 32849016
[ 6714.897343]  sdc: sdc1
[ 6747.086647] usb 3-2: reset high-speed USB device number 10 using xhci_hcd
[ 6747.247169] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6747.247175] sd 6:0:0:0: [sdc] tag#0 Sense Key : Unit Attention [current] 
[ 6747.247179] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Not ready to ready change, medium may have changed
[ 6747.247184] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 01 f5 3c 78 00 00 88 00
[ 6747.247187] print_req_error: I/O error, dev sdc, sector 32849016
[ 6747.664878]  sdc: sdc1


```

```
e2fsck -f /dev/sdc1
e2fsck 1.42.13 (17-May-2015)
e2fsck: Operation not permitted while trying to open /dev/sdc1
You must have r/w access to the filesystem or be root
root@mno:~# sudo e2fsck -f /dev/sdc1
e2fsck 1.42.13 (17-May-2015)
e2fsck: Read-only file system while trying to open /dev/sdc1
Disk write-protected; use the -n option to do a read-only
check of the device.


```
```
sudo e2fsck -n /dev/sdc1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

The short answer is no in this case, it seems micro$oft made the device read-only.

---

### Post by TheFu on 2018-03-30
**sudo fdisk -l**
that should show if there are any partitions on the device at all.  It isn't required.  For example, I routinely use dd to shove an Ubuntu ISO onto flash storage to perform installs.  No partitioning.

Check the drive using a different USB port.  Sometimes flash devices aren't compatible with the USB controllers.  Also try switching between USB2 controllers and USB3.

Lastly, when a vendor gives away a bootable flash device, they may disable writes in the firmware. After all, they want us to use their software, not delete it and reuse the device however we want.  I've seen this with vendor branded USB storage a few times, though not all that often.

---

### Post by SeijiSensei on 2018-03-30
Does the device have a physical read-only switch?

---

### Post by QIII on 2018-03-30
The company you are referring to is "Microsoft".

Thanks.

---

### Post by Yellow Pasque on 2018-03-30
> Gparted doesn't want anything to do with it

Be more specific.

---

### Post by yancek on 2018-03-30
The df command isn't useful in this situation as it only outputs information on mounted partitions and you indicate that you have not been able to mount it.
What filesystem is on it?  Running sudo fdisk -l and sudo parted -l and posting the output here would be useful.

What have you tried with GParted?  If you open it and select the CORRECT device, then go to the Device tab and create a new partition table it should work.

---

### Post by MibunoOokami on 2018-03-30
> **TheFu said:**
> **sudo fdisk -l**
that should show if there are any partitions on the device at all.  It isn't required.  For example, I routinely use dd to shove an Ubuntu ISO onto flash storage to perform installs.  No partitioning.

Check the drive using a different USB port.  Sometimes flash devices aren't compatible with the USB controllers.  Also try switching between USB2 controllers and USB3.

Lastly, when a vendor gives away a bootable flash device, they may disable writes in the firmware. After all, they want us to use their software, not delete it and reuse the device however we want.  I've seen this with vendor branded USB storage a few times, though not all that often.

I have tried other ports, I'm guessing the writes have been disabled.

> **SeijiSensei said:**
> Does the device have a physical read-only switch?

Not that I could see. I pulled it apart yesterday wondering if it might have one. If it does, it's not as obvious as the SD card feature.

> **QIII said:**
> The company you are referring to is "Microsoft".

Thanks.

Yep.

> **Temüjin said:**
> Be more specific.

Gparted just says it can't do anything because the disk is read-only

---

### Post by TheFu on 2018-03-30
**sudo fdisk -l**
???>??????

---

### Post by MibunoOokami on 2018-03-30
> **TheFu said:**
> **sudo fdisk -l**
???>??????

```
Disk /dev/sdc: 15.7 GiB, 16819159040 bytes, 32849920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 30296063 30294016 14.5G  7 HPFS/NTFS/exFAT


```

---

### Post by SeijiSensei on 2018-03-30
Have you tried to format it with mkfs?

```
sudo mkfs -t ext4 /dev/sdc1
```

e2fsck is the Linux equivalent of Windows chkdsk.  It checks the integrity of ext[234] filesystems, but it doesn't format them.

---

### Post by TheFu on 2018-03-30
So fdisk can read the device but gparted cannot?  Interesting.  I would think that if fdisk can read it, then gparted should as well.

Using fdisk, can you delete the sdc1 partition?

Would be interesting to see what **lsusb** shows too.  Maybe the controller chips/device ID will give some clues?

---

### Post by MibunoOokami on 2018-03-30
> **TheFu said:**
> So fdisk can read the device but gparted cannot?  Interesting.  I would think that if fdisk can read it, then gparted should as well.

Using fdisk, can you delete the sdc1 partition?

Would be interesting to see what **lsusb** shows too.  Maybe the controller chips/device ID will give some clues?

Sorry, no Gparted can see it, just won't delete the existing partition due to it being read-only. 

From fdisk

```
sudo fdisk /dev/sdc1

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdc1: Read-only file system

```

From lsusb
```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f2:b53e Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 13d3:3478 IMC Networks 
Bus 003 Device 003: ID 0bda:0153 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 1a2c:0e24 China Resource Semico Co., Ltd 
Bus 003 Device 007: ID 22fc:0001  
Bus 003 Device 006: ID 056e:00e3 Elecom Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by MibunoOokami on 2018-03-30
> **SeijiSensei said:**
> Have you tried to format it with mkfs?

```
sudo mkfs -t ext4 /dev/sdc1
```

e2fsck is the Linux equivalent of Windows chkdsk.  It checks the integrity of ext[234] filesystems, but it doesn't format them.

This is what I got

```
$ sudo mkfs -t ext4 /dev/sdc1
[sudo] password for mno: 
mke2fs 1.42.13 (17-May-2015)
mkfs.ext4: No such file or directory while trying to determine filesystem size

```

---

### Post by MibunoOokami on 2018-04-05
Bump

---

### Post by sudodus on 2018-04-05
Some USB flash drives are made read-only. I mean that the **drive** is read-only, which means that you cannot modify it. It is like a burned and finished CD or DVD disk.

Edit:

Other USB flash drives turn read-only as the first step in the failure process. This is sometimes called 'grid-locked'.

The following links might be helpful, maybe to make the USB drive read-write, maybe only to understand what is the problem.

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

[Pendrive lifetime](https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by MibunoOokami on 2018-04-07
> **sudodus said:**
> Some USB flash drives are made read-only. I mean that the **drive** is read-only, which means that you cannot modify it. It is like a burned and finished CD or DVD disk.

Edit:

Other USB flash drives turn read-only as the first step in the failure process. This is sometimes called 'grid-locked'.

The following links might be helpful, maybe to make the USB drive read-write, maybe only to understand what is the problem.

[Can't format my usb drive. I have already tried with mkdosfs and gparted]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035")

[Pendrive lifetime]("https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

Yep, must have been made read-only by microsoft because the first MB can't be erased but the drive is still functional for repairing windows systems.

Thanks everyone for all the advice.

---

