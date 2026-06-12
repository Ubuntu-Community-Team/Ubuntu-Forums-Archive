---
title: "Can't mount external HDD or Format it."
date: 2011-07-20
forum: Hardware
---

### Post by Cr3al on 2011-07-20
I salvaged the 120gb toshiba MK1231GAL PATA/ZIFF HDD from a broken zune (the issue was with the zune was the screen not the disk drive) . I bought a enclosure off the internet so i could use it as a external HDD, but when i plug it into my laptop running Ubuntu 11.04 i'm unable to mount the device and it won't let me format it using the disk utility application. I don't mind losing the data by formatting i just don't want to do anything that could permanently damage the device as i have little experience dealing with technical issues in linux. 


```
cereal@cereal-VGN-NS110D:~$ sudo fdisk -l
[sudo] password for cereal: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc5fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
cereal@cereal-VGN-NS110D:~$ sudo mount -t vfat /dev/sdb /mnt/usb
mount: /dev/sdb: can't read superblock
cereal@cereal-VGN-NS110D:~$ dmesg | tail -20
[97698.021208] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[97698.021215] sd 11:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[97698.021224] Info fld=0x0
[97698.021228] sd 11:0:0:0: [sdb]  Add. Sense: No additional sense information
[97698.021239] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[97698.021259] end_request: I/O error, dev sdb, sector 63
[97698.028593] sd 11:0:0:0: [sdb] Unhandled sense code
[97698.028600] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[97698.028609] sd 11:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[97698.028619] Info fld=0x0
[97698.028623] sd 11:0:0:0: [sdb]  Add. Sense: No additional sense information
[97698.028634] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[97698.028655] end_request: I/O error, dev sdb, sector 63
[97698.035189] sd 11:0:0:0: [sdb] Unhandled sense code
[97698.035196] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[97698.035204] sd 11:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
[97698.035213] Info fld=0x0
[97698.035218] sd 11:0:0:0: [sdb]  Add. Sense: No additional sense information
[97698.035228] sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 3f 00 00 08 00
[97698.035249] end_request: I/O error, dev sdb, sector 4159


```

Edit* Trying to format the drive using Disk utility gives there error "Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error"

thanks for taking the time to read this.

---

### Post by dandnsmith on 2011-07-21
You've obtained the critical information a couple of ways - it cannot read a valid partition table.
I'd try using fdisk or gparted to get the disk set up - if that is at all possible, which it may not be in view of those errors.
It seems possible that that disk is no longer usable.

---

### Post by Cr3al on 2011-07-21
> **dandnsmith said:**
>  I'd try using fdisk or gparted to get the disk set up - if that is at all possible, which it may not be in view of those errors.
It seems possible that that disk is no longer usable.

I'm starting to believe that too, I tried to Create a new partition a number of times using cfdisk Which changed the information that shows up under fdisk -l but it still gives an error when trying to mount. Would something like ```
 dd if=/dev/zero of=/dev/sda 
``` work? couldn't zeroing out the drive give it a chance at being able to format it once again? Despite the risks of using that command and wiping out the wrong drive.

---

### Post by ddastoor on 2011-07-21
Hi, 
From your code output, it looks like your mainhdd is /dev/sda and ur zune disk is /dev/sdb, right ? First of all, be VERY careful when you use dd by not wiping out your main (internal) harddisk : )

Having said that and assuming that your USB connected zune HDD is /dev/sdb
do a (also since the zune HDD is already messed up, it would not automount anyway, so there's no need to unmount it)


```
sudo fdisk /dev/sdb

```

and now trying partitioning.


After fdisk exists, for good measure : ) do 

```
sync

```


Hope this helps.

---

