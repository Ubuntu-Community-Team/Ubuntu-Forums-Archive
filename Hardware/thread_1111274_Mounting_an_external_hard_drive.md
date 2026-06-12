---
title: "Mounting an external hard drive"
date: 2009-03-30
forum: Hardware
---

### Post by moonoo on 2009-03-30
Hi, 

I seem to be slowly going mad here with Intrepid!

What we could do with easy on Hardy now seem to be a real struggle with Intrepid!

Not mentioning the waste of time my Bluetooth devices are now (apparently Bluez has had a re-write which refuses to work :( ) , my external hard drive refuses to mount!

I have a 80Gb external hard drive which is USB 2.0.

I use to plug it in and play but no more....

```

ubuntu@ubuntu:~$ lsusb
Bus 005 Device 003: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge
Bus 005 Device 002: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcabb571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 4045 MB, 4045930496 bytes
227 heads, 55 sectors/track, 632 cylinders
Units = cylinders of 12485 * 512 = 6392320 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         633     3951103+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(491, 226, 55) logical=(632, 212, 28)

```


This points at the main hdd which was 80Gb and my 4Gb pen drive but not my external hdd.

I have tried the mount command regardless that I cant see it and now am at a loss of what to do!

Can anyone help?

Thanks!!!

---

