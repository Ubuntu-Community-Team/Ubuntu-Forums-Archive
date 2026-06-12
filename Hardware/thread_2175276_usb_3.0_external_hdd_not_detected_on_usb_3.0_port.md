---
title: "usb 3.0 external hdd not detected on usb 3.0 port"
date: 2013-09-18
forum: Hardware
---

### Post by DrJohn999 on 2013-09-18
Using: Ubuntu 13.04, 3.8.0-30-generic kernel #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.

When I plug this USB 3.0 HP 1 TB external HDD into any of the USB 2.0 ports on my Asus P8Z77-V LK motherboard the drive automounts, for example:

```
$ dmesg
[1117238.717536] usb 1-1.1: new high-speed USB device number 14 using ehci-pci
[1117238.810299] usb 1-1.1: New USB device found, idVendor=03f0, idProduct=bb07
[1117238.810304] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[1117238.810307] usb 1-1.1: Product: Portable HD BB07
[1117238.810309] usb 1-1.1: Manufacturer: HP
[1117238.810311] usb 1-1.1: SerialNumber: 575832314137315838363833
[1117238.810909] scsi15 : usb-storage 1-1.1:1.0
[1117239.806235] scsi 15:0:0:0: Direct-Access     HP       Portable HD BB07 1003 PQ: 0 ANSI: 6
[1117239.807351] sd 15:0:0:0: Attached scsi generic sg9 type 0
[1117239.811770] sd 15:0:0:0: [sdj] Spinning up disk...
[1117247.438760] .ready
[1117247.439626] sd 15:0:0:0: [sdj] 1953519616 512-byte logical blocks: (1.00 TB/931 GiB)
[1117247.440729] sd 15:0:0:0: [sdj] Write Protect is off
[1117247.440734] sd 15:0:0:0: [sdj] Mode Sense: 47 00 10 08
[1117247.441708] sd 15:0:0:0: [sdj] No Caching mode page present
[1117247.441713] sd 15:0:0:0: [sdj] Assuming drive cache: write through
[1117247.444568] sd 15:0:0:0: [sdj] No Caching mode page present
[1117247.444573] sd 15:0:0:0: [sdj] Assuming drive cache: write through
[1117247.450331]  sdj: sdj1
[1117247.453416] sd 15:0:0:0: [sdj] No Caching mode page present
[1117247.453420] sd 15:0:0:0: [sdj] Assuming drive cache: write through
[1117247.453424] sd 15:0:0:0: [sdj] Attached SCSI disk
[1117248.053518] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[1117248.055253] XFS (sdj1): Mounting Filesystem
[1117248.318790] XFS (sdj1): Ending clean mount

```
Unmount the drive, unplug, then plug into the USB 3.0 port on an Atech Flash Pro-57U USB 3.0 card reader w/ front USB 3.0 port, and nothing happens. No syslog messages, nothing is detected, nothing mounts:
```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0fde:ca01  
Bus 003 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 002: ID 11b0:6558 ATECH FLASH TECHNOLOGY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver

```
A device with ID 03f0:bb07 is not present. The drive does, however, spin up and its light comes on.
Now, plug a (WD Passport) USB 2.0 external HDD into the same USB 3.0 port and it is detected, mounts OK. 
```
$ cat /var/log syslog | grep usb
Sep 18 08:18:13 p8z77v kernel: [1118143.982200] usb 3-4: new high-speed USB device number 7 using xhci_hcd
Sep 18 08:18:13 p8z77v mtp-probe: checking bus 3, device 7: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Sep 18 08:18:13 p8z77v kernel: [1118143.998956] usb 3-4: New USB device found, idVendor=1058, idProduct=0704
Sep 18 08:18:13 p8z77v kernel: [1118143.998961] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 18 08:18:13 p8z77v kernel: [1118143.998964] usb 3-4: Product: External HDD    
Sep 18 08:18:13 p8z77v kernel: [1118143.998966] usb 3-4: Manufacturer: Western Digital 
Sep 18 08:18:13 p8z77v kernel: [1118143.998969] usb 3-4: SerialNumber: 5758453430384C5938343734
Sep 18 08:18:13 p8z77v kernel: [1118143.999352] usb-storage 3-4:1.0: Quirks match for vid 1058 pid 0704: 8000
Sep 18 08:18:13 p8z77v kernel: [1118143.999395] scsi16 : usb-storage 3-4:1.0

```
and
```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0fde:ca01  
Bus 003 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 007: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 004 Device 002: ID 11b0:6558 ATECH FLASH TECHNOLOGY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

The card reader part of the Atec works: plug in an 8GB SDHC card and it is detected, mounts, r/w, etc.

Should test with another 3.0 HDD, but none on hand. Could this be a problem with 13.04 and not with the HDD?

---

### Post by TheFu on 2013-09-18
I was just looking at a HDS 4TB external USB3 drive yesterday.  Seems they did something funny in the enclosure which makes it tough to work with Linux,.  Don't know if your HP did the same or not.  I'd start doing research around the specific chips used in the external enclosure, assuming you didn't want to just take the HDD out and use it in a dock or internally mount it.

---

