---
title: "USB drives detected in lsusb but don't mount"
date: 2016-01-19
forum: Hardware
---

### Post by LiSrt on 2016-01-19
For a while now, I have been unable to mount or automount USB connected drives.

For example, if I connect my phone with USB, I see the following in dmesg:
```
[  558.148772] usb 1-5.1: new high-speed USB device number 8 using ehci-pci[  558.257878] usb 1-5.1: New USB device found, idVendor=2970, idProduct=2281
[  558.257883] usb 1-5.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  558.257886] usb 1-5.1: Product: Wileyfox Swift
[  558.257889] usb 1-5.1: Manufacturer: Wileyfox
[  558.257891] usb 1-5.1: SerialNumber: aeacefd
```

...but if I use the lsblk command, no drives show up (other than the internal ones):
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  18.7G  0 disk 
&#9500;&#9472;sda1   8:1    0   3.8G  0 part [SWAP]
&#9492;&#9472;sda2   8:2    0  14.8G  0 part /
sdb      8:16   0 298.1G  0 disk 
&#9492;&#9472;sdb1   8:17   0 298.1G  0 part /home
sr0     11:0    1  1024M  0 rom  
```

Similarly with fdisk:
```

Disk /dev/sda: 20.0 GB, 20014718976 bytes
255 heads, 63 sectors/track, 2433 cylinders, total 39091248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006fdcd


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     7999487     3998720   82  Linux swap / Solaris
/dev/sda2   *     7999488    39090175    15545344   83  Linux


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050b8a


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641   83  Linux
```

I do see the entry in lsusb ("Bus 001 Device 008: ID 2970:2281"):
```
Bus 002 Device 003: ID 046d:c326 Logitech, Inc. Bus 002 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 044f:b106 ThrustMaster, Inc. 
Bus 001 Device 008: ID 2970:2281  
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I've tried looking at some similar problems on the forum, but can't tell exactly what is going on - is there something in particular I should be doing?

Ubuntu version is:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```
Usually running XFCE, which is why I selected the "Xubuntu" prefix.

---

### Post by blueridgedog on 2016-01-19
What exactly is plugged in?  Manufacture 2970 is nonexistent in the USB registry.

---

### Post by LiSrt on 2016-01-20
> **blueridgedog said:**
> What exactly is plugged in?  Manufacture 2970 is nonexistent in the USB registry.

That was my phone - the problem happens whatever I connect though - external drives, tablets, phones, etc.

Incidentally, non-storage devices (e.g. mouse/keyboard) work fine.

---

