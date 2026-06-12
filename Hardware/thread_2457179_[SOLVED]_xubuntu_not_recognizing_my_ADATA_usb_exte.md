---
title: "[SOLVED] xubuntu not recognizing my ADATA usb external harddrive...?"
date: 2021-01-27
forum: Hardware
---

### Post by dbee on 2021-01-27
recognizing my internal hd and my microsd card no issues ...
```


dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop/hahamarketing/dara@hahamarketing.com$ sudo fdisk -l
Disk /dev/mmcblk0: 29.1 GiB, 31268536320 bytes, 61071360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 52C3523D-707F-4F3D-9321-0D620C9526C4

Device           Start      End  Sectors  Size Type
/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2 1050624 61069311 60018688 28.6G Linux filesystem


Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk1: 116.9 GiB, 125493575680 bytes, 245104640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```


dmesg | tail when i plug in the device...
```

[88382.199012] pci_bus 0000:02: Allocating resources
[116787.139730] usb 1-1: new high-speed USB device number 4 using xhci_hcd
[116792.503665] usb 1-1: device descriptor read/64, error -110
[116808.119557] usb 1-1: device descriptor read/64, error -110
[116808.355322] usb 1-1: new high-speed USB device number 5 using xhci_hcd
[116813.495950] usb 1-1: device descriptor read/64, error -110
[116829.111646] usb 1-1: device descriptor read/64, error -110
[116829.219680] usb usb1-port1: attempt power cycle
[116829.875969] usb 1-1: new high-speed USB device number 6 using xhci_hcd
[116835.127794] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[116840.507624] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[116840.715606] usb 1-1: device not accepting address 6, error -62
[116840.843710] usb 1-1: new high-speed USB device number 7 using xhci_hcd
[116845.879604] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[116851.255806] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[116851.463243] usb 1-1: device not accepting address 7, error -62
[116851.463361] usb usb1-port1: unable to enumerate USB device
[117255.811470] Lockdown: debugfs is restricted; see man kernel_lockdown.7


```

I'm running short  on disk space on my internal hd on this computer. could that be an issue perhaps?

---

### Post by dbee on 2021-01-29
I typed out a whole tutorial on my phone on fixing the issue and formatting/mounting a external hard drive. But when I pressed submit I got 'expired token' from vbulletin. And lost it all.

I've said it before. I'll say it again. This forum is completely mobile incompatible.

Suffice to say. I booted into BIOS and toggled the Secure EFI Boot setting to off. Then I formatted and mounted the external hard drive and adjusted /etc/fstab/

Not typing the whole thing out again. See 'mounting an external hard drive ubuntu' on google.

Me: frustrated.

---

