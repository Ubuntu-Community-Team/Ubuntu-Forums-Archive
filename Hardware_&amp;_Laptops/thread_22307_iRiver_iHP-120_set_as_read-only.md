---
title: "iRiver iHP-120 set as read-only"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by mthaddon on 2005-03-26
This is on an AMD64, so I'm not sure if that makes a difference, but when I plug in my iRiver iHP-120 I get the following in dmesg and as a result the file system is set to read only. Not very good as I can't copy music to it.

I have no special settings in /etc/vsftab (although I did try setting this manually for the /dev/sda1 with rw, but it still came in as read-only). I have been able to use the same device on the same laptop with SuSE 9.1 without any problem, but have since migrated to Ubuntu. 

Is this a bug?


cpu_init done, current fid 0x0, vid 0x12
ehci_hcd 0000:00:02.2: port 1 reset error -110
hub 1-0:1.0: hub_port_status failed (err = -32)
usb 1-1: new high speed USB device using ehci_hcd and address 2
usb 1-1: device descriptor read/64, error -71
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: TOSHIBA   Model: MK2004GAL         Rev: JC10
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
sda: assuming drive cache: write through
SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
FAT: Filesystem panic (dev sda1)
    fat_get_cluster: invalid cluster chain (i_pos 0)
    File system has been set read-only

---

### Post by mthaddon on 2005-04-14
Update - it needed reformatting. The filesystem had become corrupted and all I needed was to reformat it and everything looked great.

For more details, check out [https://bugzilla.ubuntu.com/show_bug.cgi?id=8428](https://bugzilla.ubuntu.com/show_bug.cgi?id=8428)

Thanks, Tom

---

