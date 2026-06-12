---
title: "Cancelled USB format - device descriptor read/64, error -110"
date: 2017-03-24
forum: Hardware
---

### Post by nymeriarya on 2017-03-24
Hi,
A week ago, I plugged in my usb drive on Linux and realized some folders and files were missing. It seemed strange, so I decided to check on Windows. When I plugged the usb on Windows, the folders and files were there, but I couldn't open them because Windows said they were corrupted or damaged. I managed to recover them with some software but decided it would be best to format the drive to prevent more file damage. When formatting through Disks Manager, it said it couldn't be completed because there was an error. I tried formatting again through the option in Computer where you can see all your disks, and unchecked the "Quick format" option just in case (yes, maybe I was stupid). After a while, the formatting got stuck and didn't advance. I had to go and couldn't leave the computer on, so I cancelled the formatting and unplugged the usb (stupid again). Now, the usb isn't recognized.

On Windows it says the usb can't be recognized but it appears on Device Manager with a little yellow triangle. I decided to see what happened on Ubuntu. 

First of all, my Ubuntu version:

```
$ lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

$ uname -a
Linux elendor-desktop 3.13.0-112-generic #159-Ubuntu SMP Fri Mar 3 15:26:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

And the usb is a 32GB Verbatim Store N Go.

It doesn't appear mounted, and these are the messages I get from dmesg:

```
[ 3972.130826] usb 2-1.2: new high-speed USB device number 23 using ehci-pci
[ 3972.225052] usb 2-1.2: New USB device found, idVendor=18a5, idProduct=0243
[ 3972.225058] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3972.225060] usb 2-1.2: Product: STORE N GO
[ 3972.225063] usb 2-1.2: Manufacturer: Verbatim
[ 3972.225065] usb 2-1.2: SerialNumber: 0263825696060077
[ 3972.225566] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[ 3972.225723] scsi12 : usb-storage 2-1.2:1.0
[ 3973.303345] usb 2-1.2: reset high-speed USB device number 23 using ehci-pci
[ 3978.377704] usb 2-1.2: device descriptor read/64, error -110
[ 3983.556073] usb 2-1.2: device descriptor read/64, error -110
[ 3983.732176] usb 2-1.2: reset high-speed USB device number 23 using ehci-pci
[ 3988.806528] usb 2-1.2: device descriptor read/64, error -110
[ 3994.160993] usb 2-1.2: reset high-speed USB device number 23 using ehci-pci
[ 4004.573820] usb 2-1.2: device not accepting address 23, error -110
[ 4004.645829] usb 2-1.2: reset high-speed USB device number 23 using ehci-pci
(...)
[ 1684.056758] scsi 11:0:0:0: Device offlined - not ready after error recovery

```

The (...) means it goes on like that until the last message. It doesn't appear listed under lsusb, not on disks or fdisk, nothing.


```
$ sudo lsusb
Bus 002 Device 007: ID 0461:4dd7 Primax Electronics, Ltd 
Bus 002 Device 006: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 002 Device 005: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 004: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 002 Device 003: ID 1395:0025 Sennheiser Communications 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2357:0101  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298,1G  0 disk 
&#9492;&#9472;sda1   8:1    0 298,1G  0 part 
sdb      8:16   0 298,1G  0 disk 
&#9500;&#9472;sdb1   8:17   0  55,9G  0 part /
&#9500;&#9472;sdb2   8:18   0   7,5G  0 part [SWAP]
&#9492;&#9472;sdb3   8:19   0 234,8G  0 part /home
sr0     11:0    1  1024M  0 rom 

```

 I've read a lot of threads on the *device descriptor read/64 error -110* error and tried everything but can't solve it. Some say it's a power-related error and disconnecting all devices plus unplugging the computer works, but not for me. Maybe it can't be solved, but I'd try anything to see if I can get it working again since it was my only usb and it barely had a year... So if anyone knows anything, please let me know. Thank you!

---

### Post by sudodus on 2017-03-24
The USB drive is ***not*** recognized as a mass storage device /dev/sdx, where x is the drive letter. it means that the repair tools available for normal users like you and me cannot connect to it. ***I suggest that you try in other computers and with other operating systems, if available.***, because there might be a mis-match between the computer and the USB drive.

The following links describe what might be possible (if the USB drive can recognized as a mass storage device /dev/sdx)

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

