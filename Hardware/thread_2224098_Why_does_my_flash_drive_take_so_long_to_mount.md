---
title: "Why does my flash drive take so long to mount?"
date: 2014-05-14
forum: Hardware
---

### Post by John_Curry on 2014-05-14
I have a 16GB USB drive that seems to take ages to mount in Ubuntu 14.04. I have formatted it several times using gparted NTFS (so I can also use on windows) but still takes a long time to mount. 

Any ideas?:confused:

---

### Post by windowsfree on 2014-05-15
i experienced something similar for my Cruzer 32 gig.  I actually formatted it for FAT32 and it was a small amount quicker.  I plugged the USB drive into Windows 7 and it was slow there also.  It maybe the drive itself or be related to the capacity of the drive.  Sorry I don't have a resolution to speed it up.

---

### Post by HiImTye on 2014-05-15
ntfs has journaling, so it should take longer to mount than FAT, or ext2. plug it in and post the output of```
lsusb; lsusb -t
```

---

### Post by John_Curry on 2014-05-16
> **HiImTye said:**
> ntfs has journaling, so it should take longer to mount than FAT, or ext2. plug it in and post the output of```
lsusb; lsusb -t
```

there you go ...
john@JohnPC:~$ lsusb; lsusb -t
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 017: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 003 Device 016: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 015: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 014: ID 0781:5535 SanDisk Corp. 
Bus 003 Device 019: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 1: Dev 19, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 2: Dev 14, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 3: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 3: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 3: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 7: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 7: Dev 3, If 1, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 7: Dev 3, If 2, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 7: Dev 3, If 3, Class=Application Specific Interface, Driver=, 12M
    |__ Port 9: Dev 15, If 0, Class=Hub, Driver=hub/3p, 480M
        |__ Port 1: Dev 16, If 0, Class=Hub, Driver=hub/3p, 480M
            |__ Port 1: Dev 17, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M



Its the scandisk one. 

I have also plugged in a Genesys 32GB Micro SD card (using a Flash card reader) and that loads instantly. I see using gparted that the 32GB SD card is formatted to Fat 32 with a 4MB unallocated partition where as the 16GB USD stick is formatted to NTFS. Is this the reason?

---

### Post by John_Curry on 2014-05-18
any thoughts?

Its a strange one as it loads perfectly fine in windows.

---

