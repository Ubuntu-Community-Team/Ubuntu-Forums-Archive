---
title: "Verbatim USB500 external HD mounting then unmounting"
date: 2008-08-11
forum: General Help
---

### Post by AndySaunders on 2008-08-11
Hello,

I'm having an issue getting my Verbatim USB500 external hard drive to stay mounted in Hardy.

My syslog says the following:

```

Aug 11 19:48:07 andy-laptop kernel: [ 4842.405018] usb 7-6: new high speed USB device using ehci_hcd and address 26
Aug 11 19:48:07 andy-laptop kernel: [ 4842.558078] usb 7-6: configuration #1 chosen from 1 choice
Aug 11 19:48:07 andy-laptop NetworkManager: <debug> [1218498487.335793] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484'). 
Aug 11 19:48:07 andy-laptop kernel: [ 4842.604761] scsi22 : SCSI emulation for USB Mass Storage devices
Aug 11 19:48:07 andy-laptop kernel: [ 4842.612829] usb-storage: device found at 26
Aug 11 19:48:07 andy-laptop kernel: [ 4842.612834] usb-storage: waiting for device to settle before scanning
Aug 11 19:48:07 andy-laptop NetworkManager: <debug> [1218498487.467708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0'). 
Aug 11 19:48:12 andy-laptop kernel: [ 4845.360919] usb-storage: device scan complete
Aug 11 19:48:12 andy-laptop kernel: [ 4845.365784] scsi 22:0:0:0: Direct-Access     SAMSUNG  HD502IJ               PQ: 0 ANSI: 2
Aug 11 19:48:12 andy-laptop kernel: [ 4845.376121] sd 22:0:0:0: [sdf] 976773168 512-byte hardware sectors (500108 MB)
Aug 11 19:48:12 andy-laptop kernel: [ 4845.378609] sd 22:0:0:0: [sdf] Write Protect is off
Aug 11 19:48:12 andy-laptop kernel: [ 4845.378615] sd 22:0:0:0: [sdf] Mode Sense: 38 00 00 00
Aug 11 19:48:12 andy-laptop kernel: [ 4845.378617] sd 22:0:0:0: [sdf] Assuming drive cache: write through
Aug 11 19:48:12 andy-laptop kernel: [ 4845.380095] sd 22:0:0:0: [sdf] 976773168 512-byte hardware sectors (500108 MB)
Aug 11 19:48:12 andy-laptop kernel: [ 4845.382467] sd 22:0:0:0: [sdf] Write Protect is off
Aug 11 19:48:12 andy-laptop kernel: [ 4845.382471] sd 22:0:0:0: [sdf] Mode Sense: 38 00 00 00
Aug 11 19:48:12 andy-laptop kernel: [ 4845.382473] sd 22:0:0:0: [sdf] Assuming drive cache: write through
Aug 11 19:48:12 andy-laptop kernel: [ 4845.382477]  sdf: sdf1
Aug 11 19:48:12 andy-laptop kernel: [ 4845.385168] sd 22:0:0:0: [sdf] Attached SCSI disk
Aug 11 19:48:12 andy-laptop kernel: [ 4845.385213] sd 22:0:0:0: Attached scsi generic sg6 type 0
Aug 11 19:48:12 andy-laptop NetworkManager: <debug> [1218498492.472220] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host'). 
Aug 11 19:48:12 andy-laptop NetworkManager: <debug> [1218498492.476833] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host_scsi_device_lun0'). 
Aug 11 19:48:12 andy-laptop NetworkManager: <debug> [1218498492.506545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 11 19:48:12 andy-laptop NetworkManager: <debug> [1218498492.639818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502IJ_16050001d484_0_0'). 
Aug 11 19:48:12 andy-laptop NetworkManager: <debug> [1218498492.747879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_12DC_3D1F'). 
Aug 11 19:48:12 andy-laptop hald: mounted /dev/sdf1 on behalf of uid 1000
Aug 11 19:48:14 andy-laptop kernel: [ 4847.090111] sd 22:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 19:48:14 andy-laptop kernel: [ 4847.090119] end_request: I/O error, dev sdf, sector 63840
Aug 11 19:48:15 andy-laptop kernel: [ 4847.885659] FAT: FAT read failed (blocknr 63777)
Aug 11 19:48:15 andy-laptop kernel: [ 4847.992850] usb 5-2: device descriptor read/64, error -71
Aug 11 19:48:15 andy-laptop kernel: [ 4848.153519] usb 5-2: device descriptor read/64, error -71
Aug 11 19:48:15 andy-laptop kernel: [ 4848.369236] usb 5-2: new full speed USB device using uhci_hcd and address 12
Aug 11 19:48:16 andy-laptop kernel: [ 4848.754494] usb 5-2: device not accepting address 12, error -71
Aug 11 19:48:16 andy-laptop kernel: [ 4848.766164] usb 5-2: new full speed USB device using uhci_hcd and address 13
Aug 11 19:48:16 andy-laptop kernel: [ 4848.826243] usb 5-2: device not accepting address 13, error -71
Aug 11 19:48:16 andy-laptop kernel: [ 4848.826286] usb 7-6: USB disconnect, address 26
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827172] Buffer I/O error on device sdf1, logical block 1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827176] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827211] Buffer I/O error on device sdf1, logical block 80
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827213] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827217] Buffer I/O error on device sdf1, logical block 119286
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827219] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827222] Buffer I/O error on device sdf1, logical block 238444
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827224] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827229] FAT: bread failed in fat_clusters_flush
Aug 11 19:48:16 andy-laptop kernel: [ 4848.827235] FAT: unable to read inode block for updating (i_pos 3815107)
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.794402] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 11 19:48:16 andy-laptop hald[5455]: forcibly attempting to lazy unmount /dev/sdf1 as enclosing drive was disconnected
Aug 11 19:48:16 andy-laptop kernel: [ 4848.862914] Buffer I/O error on device sdf1, logical block 32
Aug 11 19:48:16 andy-laptop kernel: [ 4848.862920] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop kernel: [ 4848.862929] Buffer I/O error on device sdf1, logical block 119238
Aug 11 19:48:16 andy-laptop kernel: [ 4848.862931] lost page write due to I/O error on sdf1
Aug 11 19:48:16 andy-laptop hald: unmounted /dev/sdf1 from '/media/VERBATIM' on behalf of uid 0
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.877224] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_12DC_3D1F'). 
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.888285] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HD502IJ_16050001d484_0_0'). 
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.892034] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host_scsi_device_lun0'). 
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.894543] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0_scsi_host'). 
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.914866] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484_if0'). 
Aug 11 19:48:16 andy-laptop NetworkManager: <debug> [1218498496.935877] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_18a5_216_16050001d484'). 

```

What's the best way of fixing this?

---

### Post by AndySaunders on 2008-08-11
I would also like to add -- my other USB drives (thumb drives, etc.) mount without issue.

---

### Post by AndySaunders on 2008-08-12
I thought I'd resolved this; I was wrong. Still having the same issues, though it appeared to be up for about 90 seconds this time (as opposed to about 3 the previous times).

---

