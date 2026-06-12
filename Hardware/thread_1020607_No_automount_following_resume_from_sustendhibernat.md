---
title: "No automount following resume from sustend/hibernate"
date: 2008-12-24
forum: Hardware
---

### Post by Left hand of Gaia on 2008-12-24
Good morning,

Following a resume (hibernate or suspend) most automounts fail.  

This is true for USB stick/cameras and MMC/XD/etc devices, with CDROM and DVD disks being the exception.

After a reboot, all go back to normal.

Any clues on how to sort this out.

Regards

LHoG



[[ dmesg ]]
[ 6107.572158] usb 5-3: new high speed USB device using ehci_hcd and address 2
[ 6108.223984] usb 5-3: configuration #1 chosen from 1 choice
[ 6108.352243] usbcore: registered new interface driver libusual
[ 6108.377212] Initializing USB Mass Storage driver...
[ 6108.378211] scsi2 : SCSI emulation for USB Mass Storage devices
[ 6108.378484] usb-storage: device found at 2
[ 6108.378486] usbcore: registered new interface driver usb-storage
[ 6108.378494] usb-storage: waiting for device to settle before scanning
[ 6108.378501] USB Mass Storage support registered.
[ 6113.376424] usb-storage: device scan complete
[ 6113.377622] scsi 2:0:0:0: Direct-Access     USB2.0   Mobile Disk      1.00 PQ: 0 ANSI: 2
[ 6113.381818] sd 2:0:0:0: [sdb] 3948543 512-byte hardware sectors (2022 MB)
[ 6113.382811] sd 2:0:0:0: [sdb] Write Protect is off
[ 6113.382818] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6113.382824] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6113.386186] sd 2:0:0:0: [sdb] 3948543 512-byte hardware sectors (2022 MB)
[ 6113.387185] sd 2:0:0:0: [sdb] Write Protect is off
[ 6113.387191] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 6113.387196] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 6113.387205]  sdb: sdb1
[ 6113.493181] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 6113.493553] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 6114.288728] UDF-fs: No VRS found
[ 6114.422077] ISOFS: Unable to identify CD-ROM format.
[ 6120.688004] usb 5-3: USB disconnect, address 2

---

### Post by forix on 2009-08-26
```
[19554.312148] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[19554.928121] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[19555.313691] usb 2-1.2: reset full speed USB device using uhci_hcd and address 3
[19555.729690] usb 2-1.2.2: reset full speed USB device using uhci_hcd and address 4
[19555.837744] pm_op(): usb_dev_resume+0x0/0x10 returns -19
[19555.837747] PM: Device 1-5 failed to resume: error -19
[19555.837946] PM: resume devices took 4.688 seconds
[19555.838069] PM: Finishing wakeup.
[19555.838071] Restarting tasks ... <6>usb 1-5: USB disconnect, address 7

```

Yep, I have tried adding scripts to /etc/acpi/suspend.d and /etc/acpi/resume.d and even just edit /etc/acpi/prepare.sh and resume.sh without luck. 

My UFS remote share gets mounted automatically after a resume from suspended state, as soon as the wifi gets connected. The USB (NTFS) however either mounts a second time (where the first becomes impossible to access) or just says Operation not permitted and doesn't mount at all.

I was successful at doing automounts at reboot, but not at resume, YET.

---

