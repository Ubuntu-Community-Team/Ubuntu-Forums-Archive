---
title: "Bricked U3 SanDisk Cruiser USB Drive? (Error: No medium found)"
date: 2015-08-19
forum: Hardware
---

### Post by harayz on 2015-08-19
Most of the commands returned 'No medium found' and today i saw something new when trying to tackle this issue.
This maybe my last attempt to seriously try to revive the device which i had learn so much from all the different ways to diagnose different issues from different angle. it had a similar problem of (Error: No Medium Found) in the past but i forgot how i fixed it. Below is the new cmd that i tried and i wonder if anyone can tell what else can be done here:

```
root@ubuntu:~# ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 Aug 20 00:11 /dev/sda
brw-rw---- 1 root disk 8,  1 Aug 19 23:01 /dev/sda1
brw-rw---- 1 root disk 8,  2 Aug 19 23:01 /dev/sda2
brw-rw---- 1 root disk 8,  3 Aug 19 23:01 /dev/sda3
brw-rw---- 1 root disk 8,  4 Aug 19 23:01 /dev/sda4
brw-rw---- 1 root disk 8,  5 Aug 19 23:01 /dev/sda5
brw-rw---- 1 root disk 8, 16 Aug 20 00:05 /dev/sdb
brw-rw---- 1 root disk 8, 32 Aug 20 00:05 /dev/sdc
brw------- 1 root root 8, 48 Aug 20 00:27 /dev/sdd
brw-rw---- 1 root disk 8, 64 Aug 19 23:01 /dev/sde
```

The drive in question has a different permission from all the others and i wonder if fixing that could help revice the device into usable again. I have the feeling that it is no longer usable and any information on how i can access and flash the nand partition would also be helpful. For reference, the following are most of the commands that i have tried on it with the result returned.
```

root@ubuntu:~# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13d3:5130 IMC Networks Integrated Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0421:01c7 Nokia Mobile Phones N900 (Storage Mode)
Bus 001 Device 008: ID 0781:5406 SanDisk Corp. Cruzer Micro U3

root@ubuntu:~# dd if=/dev/zero of=/dev/sdd
dd: failed to open ‘/dev/sdd’: No medium found

root@ubuntu:~# dd if=/dev/zero of=/dev/sdd bs=512 count=1
dd: failed to open ‘/dev/sdd’: No medium found

root@ubuntu:~# dd if=/dev/zero of=/dev/sdd bs=4096 conv=sync,notrunc
dd: failed to open ‘/dev/sdd’: No medium found
root@ubuntu:~# update-usbids 

```

updated usbids and tried dd with several args.

```

root@ubuntu:~# lsusb -D /dev/bus/usb/001/008
   ...
bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200
...
Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
...

```

max power 200 - does this mean anything?

```

root@ubuntu:~# testdisk /dev/sdd
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Unable to open file or device /dev/sdd

root@ubuntu:~# fsck.vfat -v /dev/sdd
fsck.fat 3.0.26 (2014-03-07)
fsck.fat 3.0.26 (2014-03-07)
open: No medium found

root@ubuntu:~# mkfs.vfat /dev/sdd
mkfs.fat 3.0.26 (2014-03-07)
/dev/sdd: No medium found

root@ubuntu:~# mkdir /mnt/sdd
root@ubuntu:~# mount /dev/sdd /mnt/sdd
mount: no medium found on /dev/sdd

root@ubuntu:~# mount -o ro,offset=$((63*512)) /dev/sdd /mnt/sdd
/dev/sdd: No medium found

root@ubuntu:~# sfdisk -l /dev/sdd
/dev/sdd: No medium found
sfdisk: cannot open /dev/sdd for reading

root@ubuntu:~# sfdisk -fl /dev/sdd
/dev/sdd: No medium found
sfdisk: cannot open /dev/sdd for reading

root@ubuntu:~# fdisk -l /dev/sdd
Error: Error opening /dev/sdd: No medium found                            
   r   Retry                                                              
   c   Cancel
r
Error: Error opening /dev/sdd: No medium found                            
   r   Retry                                                              
   c   Cancel
c
Unable to open /dev/sdd
...

...
(parted) select /dev/sdd
Error: Error opening /dev/sdd: No medium found                            
Retry/Cancel? c 

```

it wont mount and i tried all the fs type cmd that i know. 

```

root@ubuntu:~# lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0  76.4G  0 part /
&#9500;&#9472;sda2   8:2    0   7.2G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0  29.3G  0 part /sda3
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 145.2G  0 part /sda5

root@ubuntu:~# u3-tool -i /dev/sdd
Error opening device: No medium found


```

i even checked every files in /etc/udev/rules.d/ to make sure i did not accidentally blacklist the 'vendor id' or 'product id' when i mess around with rtl-sdr and adb but please let me know if there is anything else i can do and try.

---

### Post by tgalati4 on 2015-08-20
If the USB connection has been stressed, then you can't get enough power into the flash drive to make it work properly.  I would take a hot XActo knife and carefully cut away the plastic behind the USB shell.  Take the two metal halves apart and resolder the 4 connections--2 power on the outside pins, 2 data on the inside pins.  There are youtube videos on how to do it.

If it still doesn't work after resoldering, then there is possibly damage to the flash drive's controller circuitry--static electricity damage or a cosmic ray punched through the circuitry.

---

