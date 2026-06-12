---
title: "Seagate Expansion 12 TB USB3 drive - no SMART support?"
date: 2022-11-27
forum: Hardware
---

### Post by kpatz on 2022-11-27
Hey Ubuntu peeps.  I recently upgraded the drives in my primary file server and backup server to 12TB Ironwolf drives.  I also bought two Seagate Expansion 12TB external drives (STKP12000400) to use for "offsite" backups.

Previously I had 4 TB drives and used 4 TB Buffalo USB3 drives for the "offsite" backups.  These worked well, and I could use **smartctl** to monitor the health of the external drives by adding **-d sat** to the command.

However, these new Seagate drives don't seem to support SMART.  If I use -d sat, I get this error:

```

kpatz@catzfs01:~/scripts$ sudo smartctl -a /dev/sdd -d sat
[sudo] password for kpatz: 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-53-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

Read Device Identity failed: scsi error unsupported field in scsi command

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
kpatz@catzfs01:~/scripts$ 

```

I've tried other options, -d scsi seems to work the best.  But I still can't get any SMART info.

```

kpatz@catzfs01:~/scripts$ sudo smartctl -a /dev/sdd -d scsi
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-53-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               Seagate
Product:              Expansion HDD
Revision:             1801
Compliance:           SPC-4
User Capacity:        12,000,138,624,512 bytes [12.0 TB]
Logical block size:   512 bytes
Physical block size:  4096 bytes
LU is fully provisioned
Logical Unit id:      0x3e4143364350524e
Serial number:        00000000NAC6CPRN
Device type:          disk
Local Time is:        Sun Nov 27 11:21:57 2022 EST
SMART support is:     Unavailable - device lacks SMART capability.

=== START OF READ SMART DATA SECTION ===
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C

Error Counter logging not supported

No Self-tests have been logged

kpatz@catzfs01:~/scripts$ 

```
Is this a limitation of this drive/enclosure?  You'd think in 2022 a modern USB drive enclosure would support SMART.

lsusb and lsusb -t return (Bus 009 shows the 2 external drives):
```

kpatz@catzfs01:~/scripts$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 005: ID 0bc2:2038 Seagate RSS LLC Expansion HDD
Bus 009 Device 004: ID 0bc2:2038 Seagate RSS LLC Expansion HDD
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 051d:0003 American Power Conversion UPS
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kpatz@catzfs01:~/scripts$ lsusb -t
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
    |__ Port 1: Dev 4, If 0, Class=Mass Storage, Driver=uas, 5000M
    |__ Port 2: Dev 5, If 0, Class=Mass Storage, Driver=uas, 5000M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbfs, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 2: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
kpatz@catzfs01:~/scripts$ 

```

Thoughts?  Any other options to smartctl I can try?  Has anyone else used these drives with Linux?

---

### Post by TheFu on 2022-11-28
[https://www.smartmontools.org/ticket/971](https://www.smartmontools.org/ticket/971) - don't use UAS to access the storage. There's another mode.  Sorry, I don't recall what it is, but I've disabled UAS before to get USB storage working.  Vaguely remember it was a udev rule that needed changing, but don't quote me. It was over a decade ago.

---

### Post by kpatz on 2022-11-29
Thanks!  I&#8217;ll try that next time I have the external drives in the house to connect up.

Hopefully switching from UAS will also allow TRIM to work, as these are SMR drives.

---

### Post by kpatz on 2022-12-04
> **TheFu said:**
> [https://www.smartmontools.org/ticket/971](https://www.smartmontools.org/ticket/971) - don't use UAS to access the storage. There's another mode.  Sorry, I don't recall what it is, but I've disabled UAS before to get USB storage working.  Vaguely remember it was a udev rule that needed changing, but don't quote me. It was over a decade ago.This worked!  Thanks.  smartctl works now.

This is what I did.  I got the device id with lsusb, and then I issued these commands to tell the kernel not to use uas with these drives:

```

rmmod uas
rmmod usb-storage
modprobe usb-storage quirks=0bc2:2038:u

```

I then attached the external drive, and it works with smartctl now.

I still need to reboot to ensure the fix works permanently, once I do that I'll mark this thread as solved.

To make the change permanent, I created a file disable-uas.conf in /etc/modprobe.d with the contents:

```

options usb-storage quirks=0bc2:2038:u

```

And then issued the command **update-initramfs -u**

---

