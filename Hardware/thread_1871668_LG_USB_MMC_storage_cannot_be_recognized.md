---
title: "LG USB MMC storage cannot be recognized"
date: 2011-10-29
forum: Hardware
---

### Post by Uigood on 2011-10-29
My phone is identified in the windows as lG usb mmc storage, but in ubuntu 11.10 there is no response under the plug, command "lsusb" can see information about the device: "Bus 006 Device 003: ID 05c6: 1000 Qualcomm, Inc. Mass Storage Device"command  "fdisk - l" cannot find anything about the device".

I compiled the kernel, adding MMC SD support, but it can only be recognized if I plug it in at boot time, and there is no way to safely remove it:

“Error detaching: helper exited with exit code 1: Detaching device /dev/sdc

USB device: /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x08 [DRIVER_SENSE, SUGGEST_OK]
 
FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x08 [DRIVER_SENSE, SUGGEST_OK]
 
FAILED: No such file or directory”

---

