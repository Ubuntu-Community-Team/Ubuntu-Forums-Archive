---
title: "lost partition table on usb device ubuntu 12.04"
date: 2012-11-24
forum: Hardware
---

### Post by amantu on 2012-11-24
Hey guyz,

I have this problem with my usb device. I searched every forums and couldn't find a proper solution.  :|

I am running ubuntu 12.04 32 bit on a Dell vostro 1520 laptop. I was about to make a bootable usb device with the latest ubuntu version (12.10) following the  instructions.
I used 'startup disk creator'  and selected erase disk option as I thought it's a normal formatting! For some reasons it seems I lost the partition table on my usb device and I cannot use even fdisk command. 

Here are some information that I have: 
```
sudo lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 008 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 008 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 008 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 008 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 007 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 003: ID 0951:1653 Kingston Technology 

```well, my usb device is the Kingston one.

```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4da6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   616763391   308380672   83  Linux
/dev/sda2       616765438   625141759     4188161    5  Extended
/dev/sda5       616765440   625141759     4188160   82  Linux swap / Solaris

Disk /dev/sdb: 7747 MB, 7747397632 bytes
239 heads, 62 sectors/track, 1021 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37f2c876

Disk /dev/sdb doesn't contain a valid partition table
```And when I try to mount it: 
```
sudo -i
mount /dev/sdb -t vfat /mnt

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```And here is the fdisk result: 
```
fdisk /dev/sdb

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x737672b8.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): a
Partition number (1-4): 1
Warning: partition 1 has empty type

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```and after that I don't have it when I use _sudo fdisk -l _until I reconnect my usb device.
 
I'm sick of this and don't know what to do! :( 
Someone please help me. 

Thanks

---

### Post by ahallubuntu on 2012-11-24
Start up gparted (or install it in 12.04 if not already installed).  Choose the USB device and then "Create Partition Table" from the "Device" menu.

---

### Post by amantu on 2012-11-24
> **ahallubuntu said:**
> Start up gparted (or install it in 12.04 if not already installed).  Choose the USB device and then "Create Partition Table" from the "Device" menu.

Thanks man for your consideration. But I faced an error! here is what I got:

---

### Post by flavouride on 2012-11-24
perhaps "testdisk" to see if the previous partition table could be recovered

---

### Post by oldfred on 2012-11-24
You can try zeroing out the partition table or the entire MBR.

Reconfirm that flash drive is sdb as once erased it is gone.
sudo fdisk -lu

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
    

       dd if=/dev/zero of=/dev/sdb bs=512 count=1

---

### Post by amantu on 2012-11-24
> **oldfred said:**
> You can try zeroing out the partition table or the entire MBR.

Reconfirm that flash drive is sdb as once erased it is gone.
sudo fdisk -lu

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
    

       dd if=/dev/zero of=/dev/sdb bs=512 count=1

When I use dd this is the result: 
```
1+0 records in
1+0 records out
512 bytes (512 B) copied, 18.6355 s, 0.0 kB/s

```

But then it's not detectable by sudo fdisk -l or gparted until I reconnect it again.

---

### Post by oldfred on 2012-11-25
But does gparted now work as there are not partitions. Or you should be able to repartition it.

---

### Post by amantu on 2012-11-26
> **oldfred said:**
> But does gparted now work as there are not partitions. Or you should be able to repartition it.

even after this Gparted still not working. The usb is still not detectable by gparted or fdisk. 

I found another usb with the same problem form a friend of. That one had problem with the partition table as well. I managed to fix that one with gparted by creating a partition table and making new partition. 

So I conclude that the problem is with the bad quality of my usb. :) 

If someone has new idea to solve this I would be glad to try it! ;) 

Thank to you all for your helps. 
Cheers!

---

