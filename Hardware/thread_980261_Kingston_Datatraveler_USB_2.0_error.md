---
title: "Kingston Datatraveler USB 2.0 error"
date: 2008-11-12
forum: Hardware
---

### Post by jpmneofito@gmail.com on 2008-11-12
Hi,

I've buyed a Kingston Datatraveler 16GB flash disk and the disk doesn't work in USB 2.0 mode in my pc at home. The pc is a AMD Phenom 9750 and the MB is a Asus M3A, and it runs Ubuntu 8.04. Another disk I have, a Sony Microvault 4GB, work correctly at full speed.

But in my pc at work, with Ubuntu 7.04, such problems doesn't happen.


Below are some logs I've found:

```


kern.log =======================================================================

Nov 12 19:27:56 jp-desktop kernel: [  149.251752]  sdd: sdd1
Nov 12 19:27:56 jp-desktop kernel: [  149.474956] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Nov 12 19:27:56 jp-desktop kernel: [  149.474992] sd 7:0:0:0: Attached scsi generic sg4 type 0
Nov 12 19:29:37 jp-desktop kernel: [  250.543086] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:29:52 jp-desktop kernel: [  265.624121] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:07 jp-desktop kernel: [  280.808954] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:08 jp-desktop kernel: [  281.024508] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:23 jp-desktop kernel: [  296.105555] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:38 jp-desktop kernel: [  311.290380] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:38 jp-desktop kernel: [  311.505936] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:48 jp-desktop kernel: [  321.892609] usb 6-4: device not accepting address 3, error -110
Nov 12 19:30:49 jp-desktop kernel: [  322.004381] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391056] usb 6-4: device not accepting address 3, error -110
Nov 12 19:30:59 jp-desktop kernel: [  332.391085] usb 6-4: USB disconnect, address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391318] sd 7:0:0:0: Device offlined - not ready after error recovery
Nov 12 19:30:59 jp-desktop kernel: [  332.391670] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.391677] end_request: I/O error, dev sdd, sector 1003808
Nov 12 19:30:59 jp-desktop kernel: [  332.392781] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.392787] end_request: I/O error, dev sdd, sector 1004000
Nov 12 19:30:59 jp-desktop kernel: [  332.394850] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.394856] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.394859] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.394893] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.394895] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop kernel: [  332.394897] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:30:59 jp-desktop kernel: [  332.395026] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.395028] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.395030] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.395038] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.395040] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop kernel: [  332.395041] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:30:59 jp-desktop kernel: [  332.405800] Buffer I/O error on device sdd1, logical block 1
Nov 12 19:30:59 jp-desktop kernel: [  332.405808] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405811] Buffer I/O error on device sdd1, logical block 505
Nov 12 19:30:59 jp-desktop kernel: [  332.405813] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405815] Buffer I/O error on device sdd1, logical block 506
Nov 12 19:30:59 jp-desktop kernel: [  332.405816] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405819] Buffer I/O error on device sdd1, logical block 526
Nov 12 19:30:59 jp-desktop kernel: [  332.405820] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405878] Buffer I/O error on device sdd1, logical block 528
Nov 12 19:30:59 jp-desktop kernel: [  332.405880] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.406090] FAT: bread failed in fat_clusters_flush
Nov 12 19:30:59 jp-desktop kernel: [  332.406098] FAT: unable to read inode block for updating (i_pos 492304)
Nov 12 19:30:59 jp-desktop kernel: [  332.412995] FAT: FAT read failed (blocknr 2760)
Nov 12 19:30:59 jp-desktop kernel: [  332.413019] FAT: FAT read failed (blocknr 505)
Nov 12 19:30:59 jp-desktop kernel: [  332.413029] FAT: unable to read inode block for updating (i_pos 492304)
Nov 12 19:30:59 jp-desktop kernel: [  332.523826] usb 6-4: new high speed USB device using ehci_hcd and address 4
Nov 12 19:31:14 jp-desktop kernel: [  347.599848] usb 6-4: device descriptor read/64, error -110
Nov 12 19:31:29 jp-desktop kernel: [  362.784667] usb 6-4: device descriptor read/64, error -110


auth.log =======================================================================
Nov 12 19:27:56 jp-desktop gnome-keyring-daemon[6044]: adding removable location: volume_uuid_20CB_8E23 at /media/disk-2
Nov 12 19:30:59 jp-desktop gnome-keyring-daemon[6044]: Error retrieving volume.is_mounted on '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23': Error: 'org.freedesktop.Hal.NoSuchDevice' Message: 'No device with id /org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'
Nov 12 19:30:59 jp-desktop gnome-keyring-daemon[6044]: removing removable location: volume_uuid_20CB_8E23


daemon.log =====================================================================
Nov 12 19:27:50 jp-desktop NetworkManager: <debug> [1226525270.990760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 
Nov 12 19:27:51 jp-desktop NetworkManager: <debug> [1226525271.042965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.045282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.046648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.221505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.632884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.681159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:27:56 jp-desktop hald: mounted /dev/sdd1 on behalf of uid 1000
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.516131] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:30:59 jp-desktop hald[5604]: forcibly attempting to lazy unmount /dev/sdd1 as enclosing drive was disconnected
Nov 12 19:30:59 jp-desktop hald: unmounted /dev/sdd1 from '/media/disk-2' on behalf of uid 0
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.560921] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561000] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561619] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561890] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562105] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562552] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 


debug ==========================================================================
Nov 12 19:27:50 jp-desktop kernel: [  144.256207] usb-storage: device found at 3
Nov 12 19:27:50 jp-desktop kernel: [  144.256210] usb-storage: waiting for device to settle before scanning
Nov 12 19:27:50 jp-desktop NetworkManager: <debug> [1226525270.990760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 
Nov 12 19:27:51 jp-desktop NetworkManager: <debug> [1226525271.042965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:27:55 jp-desktop kernel: [  149.244767] usb-storage: device scan complete
Nov 12 19:27:55 jp-desktop kernel: [  149.247119] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Nov 12 19:27:55 jp-desktop kernel: [  149.251746] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.045282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.046648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.221505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.632884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.681159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:30:59 jp-desktop kernel: [  332.394895] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop kernel: [  332.395040] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.516131] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.560921] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561000] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561619] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561890] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562105] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562552] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 


messages =======================================================================
Nov 12 19:27:50 jp-desktop kernel: [  144.121549] usb 6-4: new high speed USB device using ehci_hcd and address 3
Nov 12 19:27:50 jp-desktop kernel: [  144.255865] usb 6-4: configuration #1 chosen from 1 choice
Nov 12 19:27:50 jp-desktop kernel: [  144.256093] scsi7 : SCSI emulation for USB Mass Storage devices
Nov 12 19:27:55 jp-desktop kernel: [  149.245256] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Nov 12 19:27:55 jp-desktop kernel: [  149.246488] sd 7:0:0:0: [sdd] 31506432 512-byte hardware sectors (16131 MB)
Nov 12 19:27:55 jp-desktop kernel: [  149.247115] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:27:55 jp-desktop kernel: [  149.249733] sd 7:0:0:0: [sdd] 31506432 512-byte hardware sectors (16131 MB)
Nov 12 19:27:55 jp-desktop kernel: [  149.251741] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:27:56 jp-desktop kernel: [  149.251752]  sdd: sdd1
Nov 12 19:27:56 jp-desktop kernel: [  149.474956] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Nov 12 19:27:56 jp-desktop kernel: [  149.474992] sd 7:0:0:0: Attached scsi generic sg4 type 0
Nov 12 19:29:37 jp-desktop kernel: [  250.543086] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:08 jp-desktop kernel: [  281.024508] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:38 jp-desktop kernel: [  311.505936] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:49 jp-desktop kernel: [  322.004381] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391085] usb 6-4: USB disconnect, address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391318] sd 7:0:0:0: Device offlined - not ready after error recovery
Nov 12 19:30:59 jp-desktop kernel: [  332.391670] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.391677] end_request: I/O error, dev sdd, sector 1003808
Nov 12 19:30:59 jp-desktop kernel: [  332.392781] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.392787] end_request: I/O error, dev sdd, sector 1004000
Nov 12 19:30:59 jp-desktop kernel: [  332.394850] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.394856] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.394859] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.394893] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.395026] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.395028] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.395030] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.395038] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.405808] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405813] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405816] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405820] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405880] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.523826] usb 6-4: new high speed USB device using ehci_hcd and address 4


syslog =========================================================================
Nov 12 19:27:50 jp-desktop kernel: [  144.121549] usb 6-4: new high speed USB device using ehci_hcd and address 3
Nov 12 19:27:50 jp-desktop kernel: [  144.255865] usb 6-4: configuration #1 chosen from 1 choice
Nov 12 19:27:50 jp-desktop kernel: [  144.256093] scsi7 : SCSI emulation for USB Mass Storage devices
Nov 12 19:27:50 jp-desktop kernel: [  144.256207] usb-storage: device found at 3
Nov 12 19:27:50 jp-desktop kernel: [  144.256210] usb-storage: waiting for device to settle before scanning
Nov 12 19:27:50 jp-desktop NetworkManager: <debug> [1226525270.990760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 
Nov 12 19:27:51 jp-desktop NetworkManager: <debug> [1226525271.042965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:27:55 jp-desktop kernel: [  149.244767] usb-storage: device scan complete
Nov 12 19:27:55 jp-desktop kernel: [  149.245256] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Nov 12 19:27:55 jp-desktop kernel: [  149.246488] sd 7:0:0:0: [sdd] 31506432 512-byte hardware sectors (16131 MB)
Nov 12 19:27:55 jp-desktop kernel: [  149.247115] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:27:55 jp-desktop kernel: [  149.247119] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Nov 12 19:27:55 jp-desktop kernel: [  149.247122] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:27:55 jp-desktop kernel: [  149.249733] sd 7:0:0:0: [sdd] 31506432 512-byte hardware sectors (16131 MB)
Nov 12 19:27:55 jp-desktop kernel: [  149.251741] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:27:55 jp-desktop kernel: [  149.251746] sd 7:0:0:0: [sdd] Mode Sense: 23 00 00 00
Nov 12 19:27:55 jp-desktop kernel: [  149.251749] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.045282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.046648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:27:56 jp-desktop kernel: [  149.251752]  sdd: sdd1
Nov 12 19:27:56 jp-desktop kernel: [  149.474956] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Nov 12 19:27:56 jp-desktop kernel: [  149.474992] sd 7:0:0:0: Attached scsi generic sg4 type 0
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.221505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.632884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:27:56 jp-desktop NetworkManager: <debug> [1226525276.681159] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:27:56 jp-desktop hald: mounted /dev/sdd1 on behalf of uid 1000
Nov 12 19:29:37 jp-desktop kernel: [  250.543086] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:29:52 jp-desktop kernel: [  265.624121] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:07 jp-desktop kernel: [  280.808954] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:08 jp-desktop kernel: [  281.024508] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:23 jp-desktop kernel: [  296.105555] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:38 jp-desktop kernel: [  311.290380] usb 6-4: device descriptor read/64, error -110
Nov 12 19:30:38 jp-desktop kernel: [  311.505936] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:48 jp-desktop kernel: [  321.892609] usb 6-4: device not accepting address 3, error -110
Nov 12 19:30:49 jp-desktop kernel: [  322.004381] usb 6-4: reset high speed USB device using ehci_hcd and address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391056] usb 6-4: device not accepting address 3, error -110
Nov 12 19:30:59 jp-desktop kernel: [  332.391085] usb 6-4: USB disconnect, address 3
Nov 12 19:30:59 jp-desktop kernel: [  332.391318] sd 7:0:0:0: Device offlined - not ready after error recovery
Nov 12 19:30:59 jp-desktop kernel: [  332.391670] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.391677] end_request: I/O error, dev sdd, sector 1003808
Nov 12 19:30:59 jp-desktop kernel: [  332.392781] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.392787] end_request: I/O error, dev sdd, sector 1004000
Nov 12 19:30:59 jp-desktop kernel: [  332.394850] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.394856] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.394859] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.394893] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.394895] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop kernel: [  332.394897] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:30:59 jp-desktop kernel: [  332.395026] sd 7:0:0:0: [sdd] READ CAPACITY failed
Nov 12 19:30:59 jp-desktop kernel: [  332.395028] sd 7:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:30:59 jp-desktop kernel: [  332.395030] sd 7:0:0:0: [sdd] Sense not available.
Nov 12 19:30:59 jp-desktop kernel: [  332.395038] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:30:59 jp-desktop kernel: [  332.395040] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Nov 12 19:30:59 jp-desktop kernel: [  332.395041] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.516131] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 12 19:30:59 jp-desktop kernel: [  332.405800] Buffer I/O error on device sdd1, logical block 1
Nov 12 19:30:59 jp-desktop kernel: [  332.405808] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405811] Buffer I/O error on device sdd1, logical block 505
Nov 12 19:30:59 jp-desktop kernel: [  332.405813] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405815] Buffer I/O error on device sdd1, logical block 506
Nov 12 19:30:59 jp-desktop kernel: [  332.405816] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405819] Buffer I/O error on device sdd1, logical block 526
Nov 12 19:30:59 jp-desktop kernel: [  332.405820] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.405878] Buffer I/O error on device sdd1, logical block 528
Nov 12 19:30:59 jp-desktop kernel: [  332.405880] lost page write due to I/O error on sdd1
Nov 12 19:30:59 jp-desktop kernel: [  332.406090] FAT: bread failed in fat_clusters_flush
Nov 12 19:30:59 jp-desktop kernel: [  332.406098] FAT: unable to read inode block for updating (i_pos 492304)
Nov 12 19:30:59 jp-desktop hald[5604]: forcibly attempting to lazy unmount /dev/sdd1 as enclosing drive was disconnected
Nov 12 19:30:59 jp-desktop kernel: [  332.412995] FAT: FAT read failed (blocknr 2760)
Nov 12 19:30:59 jp-desktop kernel: [  332.413019] FAT: FAT read failed (blocknr 505)
Nov 12 19:30:59 jp-desktop kernel: [  332.413029] FAT: unable to read inode block for updating (i_pos 492304)
Nov 12 19:30:59 jp-desktop hald: unmounted /dev/sdd1 from '/media/disk-2' on behalf of uid 0
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.560921] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_20CB_8E23'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561000] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTraveler_2_0_0014780D8CF15A891011004E_0_0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561619] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host_scsi_device_lun0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.561890] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0_scsi_host'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562105] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E_if0'). 
Nov 12 19:30:59 jp-desktop NetworkManager: <debug> [1226525459.562552] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1607_0014780D8CF15A891011004E'). 
Nov 12 19:30:59 jp-desktop kernel: [  332.523826] usb 6-4: new high speed USB device using ehci_hcd and address 4
Nov 12 19:31:14 jp-desktop kernel: [  347.599848] usb 6-4: device descriptor read/64, error -110
Nov 12 19:31:29 jp-desktop kernel: [  362.784667] usb 6-4: device descriptor read/64, error -110
Nov 12 19:31:30 jp-desktop kernel: [  363.000220] usb 6-4: new high speed USB device using ehci_hcd and address 5

```

Any idea?

---

### Post by strutzz on 2008-11-24
I have the same problem with a Kingston datatraveler on 8.04. I tried the method from [Kingston FAQ]("http://www.kingston.com/support/USBFLASHDRIVES/FAQ/faq_dti_hs_2.asp") and no result, tried editing fstab and it worked for a while but then stoped , in dmesg i get > [  262.350953] usb 1-2: new full speed USB device using uhci_hcd and address 12
[  262.758353] usb 1-2: device not accepting address 12, error -32
 .
I have no idea yet .

---

### Post by jmiguel77 on 2009-05-13
hi i have the same problem

in intrepid (and previous) i could make my usb work by:

sudo modprobe -r ehci_hcd

that way i could mount my usb, with the problem it mounted as usb 1.0, but at least i could use it

when i upgraded to jaunty, and booted the 2.6.27-7-generic kernel, the same thing happened; i had to shut down the ehci_hcd module to make the usb work

now, i am booting the 2.6.28-11-generic kernel and the usb is not working; when i try the modprobe "solution", the system gives me this message

FATAL: Module ehci_hcd not found.

but in the dmesg output i can see this line:

new high speed USB device using ehci_hcd and address 17

so, what the hell is going on ???

does anybody in the ubuntu team gives a damn about this problem ?? because all i can see is complaints about bugs like this but no real solution

what a crap !!!!!

---

### Post by zampes on 2009-05-17
Hey guys!
Forget about it guys, it's a problem with the pendrive, not with your machines or the kernel or anything. It's a problem you'll have only with kingston DT 16GB of a certain model... I was there myself

[http://ubuntuforums.org/showthread.php?t=1148922&highlight=pen+automatic+unmount](http://ubuntuforums.org/showthread.php?t=1148922&highlight=pen+automatic+unmount) 

and so were others...

[http://ubuntuforums.org/showthread.php?t=1016286&highlight=kingston+16gb](http://ubuntuforums.org/showthread.php?t=1016286&highlight=kingston+16gb)
[http://ubuntuforums.org/showthread.php?t=985285&highlight=kingston+16gb](http://ubuntuforums.org/showthread.php?t=985285&highlight=kingston+16gb)

---

### Post by skr222 on 2009-05-17
To get my 8 GB Corsair Voyager USB stick to mount in Debian and Ubuntu I have to change the following value from the default 5 seconds to something like 9 with this command:

sudo echo 9 > /sys/module/scsi_mod/parameters/inq_timeout

For me this has solved the problem but the change doesn't stick between reboots in Ubuntu as it does in Debian.

---

### Post by jmiguel77 on 2009-05-26
I have tried everything i found to make this work, but nothing so far ...
I am in an newly installe jaunty and this is what i get

if i stick my kingston datatraveler 2GB at first, this is the dmesg

```
[   56.164013] usb 1-6: new high speed USB device using ehci_hcd and address 5
[   56.298664] usb 1-6: configuration #1 chosen from 1 choice
[   56.298901] scsi6 : SCSI emulation for USB Mass Storage devices
[   56.299163] usb-storage: device found at 5
[   56.299165] usb-storage: waiting for device to settle before scanning
[   61.296598] usb-storage: device scan complete
[   61.297591] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[   61.298697] sd 6:0:0:0: [sdd] 3987456 512-byte hardware sectors: (2.04 GB/1.90 GiB)
[   61.299193] sd 6:0:0:0: [sdd] Write Protect is off
[   61.299195] sd 6:0:0:0: [sdd] Mode Sense: 23 00 00 00
[   61.299197] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[   61.302070] sd 6:0:0:0: [sdd] 3987456 512-byte hardware sectors: (2.04 GB/1.90 GiB)
[   61.302905] sd 6:0:0:0: [sdd] Write Protect is off
[   61.302907] sd 6:0:0:0: [sdd] Mode Sense: 23 00 00 00
[   61.302908] sd 6:0:0:0: [sdd] Assuming drive cache: write through
```

after i try to copy a 300MB file i get this

```
[   61.302910]  sdd: sdd1
[   61.537536] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[   61.537585] sd 6:0:0:0: Attached scsi generic sg4 type 0
[  126.928013] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  130.660011] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  175.928012] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  179.368011] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  181.908012] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  197.020014] usb 1-6: device descriptor read/64, error -110
[  212.236010] usb 1-6: device descriptor read/64, error -110
[  212.452009] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  227.564011] usb 1-6: device descriptor read/64, error -110
[  242.780013] usb 1-6: device descriptor read/64, error -110
[  242.996010] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  253.404008] usb 1-6: device not accepting address 5, error -110
[  253.516013] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[  263.924008] usb 1-6: device not accepting address 5, error -110
[  263.924032] usb 1-6: USB disconnect, address 5
[  263.925023] sd 6:0:0:0: Device offlined - not ready after error recovery
[  263.925035] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.925038] end_request: I/O error, dev sdd, sector 211856
[  263.926095] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.926097] end_request: I/O error, dev sdd, sector 211904
[  263.926112] Buffer I/O error on device sdd1, logical block 8
[  263.926113] lost page write due to I/O error on sdd1
[  263.926115] Buffer I/O error on device sdd1, logical block 9
[  263.926116] lost page write due to I/O error on sdd1
[  263.926118] Buffer I/O error on device sdd1, logical block 10
[  263.926119] lost page write due to I/O error on sdd1
[  263.926121] Buffer I/O error on device sdd1, logical block 11
[  263.926122] lost page write due to I/O error on sdd1
[  263.926124] Buffer I/O error on device sdd1, logical block 12
[  263.926125] lost page write due to I/O error on sdd1
[  263.926126] Buffer I/O error on device sdd1, logical block 13
[  263.926128] lost page write due to I/O error on sdd1
[  263.926129] Buffer I/O error on device sdd1, logical block 14
[  263.926130] lost page write due to I/O error on sdd1
[  263.926132] Buffer I/O error on device sdd1, logical block 15
[  263.926133] lost page write due to I/O error on sdd1
[  263.926135] Buffer I/O error on device sdd1, logical block 16
[  263.926136] lost page write due to I/O error on sdd1
[  263.926138] Buffer I/O error on device sdd1, logical block 17
[  263.926139] lost page write due to I/O error on sdd1
[  263.926756] FAT: unable to read inode block for updating (i_pos 7827)
[  263.926808] FAT: FAT read failed (blocknr 20)
[  263.926827] FAT: FAT read failed (blocknr 8)
[  263.926832] FAT: unable to read inode block for updating (i_pos 7827)
[  263.926868] FAT: FAT read failed (blocknr 20)
[  263.926882] FAT: FAT read failed (blocknr 8)
[  263.926887] FAT: unable to read inode block for updating (i_pos 7827)
[  263.932321] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  263.932323] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.932326] sd 6:0:0:0: [sdd] Sense not available.
[  263.932335] sd 6:0:0:0: [sdd] Write Protect is off
[  263.932337] sd 6:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  263.932338] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  263.932396] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  263.932397] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.932399] sd 6:0:0:0: [sdd] Sense not available.
[  263.932407] sd 6:0:0:0: [sdd] Write Protect is off
[  263.932409] sd 6:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  263.932410] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  263.938452] FAT: unable to read inode block for updating (i_pos 7827)
[  263.944160] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  263.944162] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.944165] sd 6:0:0:0: [sdd] Sense not available.
[  263.944174] sd 6:0:0:0: [sdd] Write Protect is off
[  263.944175] sd 6:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  263.944177] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  263.947483] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  263.947485] sd 6:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  263.947487] sd 6:0:0:0: [sdd] Sense not available.
[  263.947495] sd 6:0:0:0: [sdd] Write Protect is off
[  263.947497] sd 6:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  263.947498] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  264.112016] usb 1-6: new high speed USB device using ehci_hcd and address 6
```

Then i tried the suggested workarounds (old_scheme_first, autosuspend, inq_timeout) with no success and get dmesg with this

```
[  299.077103]  sdd: sdd1
[  299.319066] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[  299.319115] sd 10:0:0:0: Attached scsi generic sg4 type 0
[  381.308018] usb 1-6: reset high speed USB device using ehci_hcd and address 9
[  383.848012] usb 1-6: reset high speed USB device using ehci_hcd and address 9
[  414.112016] usb 1-6: reset high speed USB device using ehci_hcd and address 9
[  414.244984] usb 1-6: device firmware changed
[  414.245003] usb 1-6: USB disconnect, address 9
[  414.245018] sd 10:0:0:0: Device offlined - not ready after error recovery
[  414.245028] sd 10:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  414.245032] end_request: I/O error, dev sdd, sector 123448
[  414.245057] sd 10:0:0:0: rejecting I/O to offline device
[  414.245070] sd 10:0:0:0: rejecting I/O to offline device
[  414.245074] sd 10:0:0:0: rejecting I/O to offline device
[  414.245089] sd 10:0:0:0: rejecting I/O to offline device
[  414.245103] sd 10:0:0:0: rejecting I/O to offline device
[  414.245118] sd 10:0:0:0: rejecting I/O to offline device
[  414.245133] sd 10:0:0:0: rejecting I/O to offline device
[  414.245151] sd 10:0:0:0: rejecting I/O to offline device
[  414.245162] sd 10:0:0:0: rejecting I/O to offline device
[  414.245172] sd 10:0:0:0: rejecting I/O to offline device
[  414.245182] sd 10:0:0:0: rejecting I/O to offline device
[  414.245192] sd 10:0:0:0: rejecting I/O to offline device
[  414.245194] sd 10:0:0:0: rejecting I/O to offline device
[  414.245210] sd 10:0:0:0: rejecting I/O to offline device
[  414.245221] sd 10:0:0:0: rejecting I/O to offline device
[  414.245232] sd 10:0:0:0: rejecting I/O to offline device
[  414.245242] sd 10:0:0:0: rejecting I/O to offline device
[  414.245252] sd 10:0:0:0: rejecting I/O to offline device
[  414.245261] sd 10:0:0:0: rejecting I/O to offline device
[  414.245270] sd 10:0:0:0: rejecting I/O to offline device
[  414.245279] sd 10:0:0:0: rejecting I/O to offline device
[  414.245288] sd 10:0:0:0: rejecting I/O to offline device
[  414.245297] sd 10:0:0:0: rejecting I/O to offline device
[  414.245306] sd 10:0:0:0: rejecting I/O to offline device
[  414.245315] sd 10:0:0:0: rejecting I/O to offline device
[  414.245323] sd 10:0:0:0: rejecting I/O to offline device
[  414.245332] sd 10:0:0:0: rejecting I/O to offline device
[  414.245342] sd 10:0:0:0: rejecting I/O to offline device
[  414.245353] sd 10:0:0:0: rejecting I/O to offline device
[  414.245365] sd 10:0:0:0: rejecting I/O to offline device
[  414.245376] sd 10:0:0:0: rejecting I/O to offline device
[  414.245385] sd 10:0:0:0: rejecting I/O to offline device
[  414.245394] sd 10:0:0:0: rejecting I/O to offline device
[  414.245404] sd 10:0:0:0: rejecting I/O to offline device
[  414.245413] sd 10:0:0:0: rejecting I/O to offline device
[  414.245422] sd 10:0:0:0: rejecting I/O to offline device
[  414.245431] sd 10:0:0:0: rejecting I/O to offline device
[  414.245440] sd 10:0:0:0: rejecting I/O to offline device
[  414.245450] sd 10:0:0:0: rejecting I/O to offline device
[  414.245459] sd 10:0:0:0: rejecting I/O to offline device
[  414.245468] sd 10:0:0:0: rejecting I/O to offline device
[  414.245478] sd 10:0:0:0: rejecting I/O to offline device
[  414.245487] sd 10:0:0:0: rejecting I/O to offline device
[  414.245497] sd 10:0:0:0: rejecting I/O to offline device
[  414.245506] sd 10:0:0:0: rejecting I/O to offline device
[  414.245518] sd 10:0:0:0: rejecting I/O to offline device
[  414.245527] sd 10:0:0:0: rejecting I/O to offline device
[  414.245536] sd 10:0:0:0: rejecting I/O to offline device
[  414.245545] sd 10:0:0:0: rejecting I/O to offline device
[  414.245554] sd 10:0:0:0: rejecting I/O to offline device
[  414.245563] sd 10:0:0:0: rejecting I/O to offline device
[  414.245572] sd 10:0:0:0: rejecting I/O to offline device
[  414.245580] sd 10:0:0:0: rejecting I/O to offline device
[  414.245590] sd 10:0:0:0: rejecting I/O to offline device
[  414.245599] sd 10:0:0:0: rejecting I/O to offline device
[  414.245609] sd 10:0:0:0: rejecting I/O to offline device
[  414.245618] sd 10:0:0:0: rejecting I/O to offline device
[  414.245627] sd 10:0:0:0: rejecting I/O to offline device
[  414.245636] sd 10:0:0:0: rejecting I/O to offline device
[  414.245645] sd 10:0:0:0: rejecting I/O to offline device
[  414.245655] sd 10:0:0:0: rejecting I/O to offline device
[  414.245666] sd 10:0:0:0: rejecting I/O to offline device
[  414.245675] sd 10:0:0:0: rejecting I/O to offline device
[  414.245685] sd 10:0:0:0: rejecting I/O to offline device
[  414.245689] sd 10:0:0:0: rejecting I/O to offline device
[  414.245698] sd 10:0:0:0: rejecting I/O to offline device
[  414.245707] sd 10:0:0:0: rejecting I/O to offline device
[  414.245716] sd 10:0:0:0: rejecting I/O to offline device
[  414.245725] sd 10:0:0:0: rejecting I/O to offline device
[  414.245734] sd 10:0:0:0: rejecting I/O to offline device
[  414.245743] sd 10:0:0:0: rejecting I/O to offline device
[  414.245752] sd 10:0:0:0: rejecting I/O to offline device
[  414.245762] sd 10:0:0:0: rejecting I/O to offline device
[  414.245771] sd 10:0:0:0: rejecting I/O to offline device
[  414.245780] sd 10:0:0:0: rejecting I/O to offline device
[  414.245789] sd 10:0:0:0: rejecting I/O to offline device
[  414.245798] sd 10:0:0:0: rejecting I/O to offline device
[  414.245810] sd 10:0:0:0: rejecting I/O to offline device
[  414.245819] sd 10:0:0:0: rejecting I/O to offline device
[  414.245827] sd 10:0:0:0: rejecting I/O to offline device
[  414.245836] sd 10:0:0:0: rejecting I/O to offline device
[  414.245845] sd 10:0:0:0: rejecting I/O to offline device
[  414.245855] sd 10:0:0:0: rejecting I/O to offline device
[  414.245863] sd 10:0:0:0: rejecting I/O to offline device
[  414.245872] sd 10:0:0:0: rejecting I/O to offline device
[  414.245881] sd 10:0:0:0: rejecting I/O to offline device
[  414.245890] sd 10:0:0:0: rejecting I/O to offline device
[  414.245899] sd 10:0:0:0: rejecting I/O to offline device
[  414.245908] sd 10:0:0:0: rejecting I/O to offline device
[  414.245918] sd 10:0:0:0: rejecting I/O to offline device
[  414.245927] sd 10:0:0:0: rejecting I/O to offline device
[  414.245936] sd 10:0:0:0: rejecting I/O to offline device
[  414.245945] sd 10:0:0:0: rejecting I/O to offline device
[  414.245956] sd 10:0:0:0: rejecting I/O to offline device
[  414.245965] sd 10:0:0:0: rejecting I/O to offline device
[  414.245975] sd 10:0:0:0: rejecting I/O to offline device
[  414.245984] sd 10:0:0:0: rejecting I/O to offline device
[  414.245992] sd 10:0:0:0: rejecting I/O to offline device
[  414.246002] sd 10:0:0:0: rejecting I/O to offline device
[  414.246011] sd 10:0:0:0: rejecting I/O to offline device
[  414.246020] sd 10:0:0:0: rejecting I/O to offline device
[  414.246028] sd 10:0:0:0: rejecting I/O to offline device
[  414.246037] sd 10:0:0:0: rejecting I/O to offline device
[  414.246046] sd 10:0:0:0: rejecting I/O to offline device
[  414.246055] sd 10:0:0:0: rejecting I/O to offline device
[  414.246063] sd 10:0:0:0: rejecting I/O to offline device
[  414.246072] sd 10:0:0:0: rejecting I/O to offline device
[  414.246082] sd 10:0:0:0: rejecting I/O to offline device
[  414.246091] sd 10:0:0:0: rejecting I/O to offline device
[  414.246102] sd 10:0:0:0: rejecting I/O to offline device
[  414.246111] sd 10:0:0:0: rejecting I/O to offline device
[  414.246120] sd 10:0:0:0: rejecting I/O to offline device
[  414.246129] sd 10:0:0:0: rejecting I/O to offline device
[  414.246138] sd 10:0:0:0: rejecting I/O to offline device
[  414.246147] sd 10:0:0:0: rejecting I/O to offline device
[  414.246156] sd 10:0:0:0: rejecting I/O to offline device
[  414.246159] sd 10:0:0:0: rejecting I/O to offline device
[  414.246168] sd 10:0:0:0: rejecting I/O to offline device
[  414.246176] sd 10:0:0:0: rejecting I/O to offline device
[  414.246186] sd 10:0:0:0: rejecting I/O to offline device
[  414.246195] sd 10:0:0:0: rejecting I/O to offline device
[  414.246204] sd 10:0:0:0: rejecting I/O to offline device
[  414.246212] sd 10:0:0:0: rejecting I/O to offline device
[  414.246221] sd 10:0:0:0: rejecting I/O to offline device
[  414.246230] sd 10:0:0:0: rejecting I/O to offline device
[  414.246241] sd 10:0:0:0: rejecting I/O to offline device
[  414.246250] sd 10:0:0:0: rejecting I/O to offline device
[  414.246259] sd 10:0:0:0: rejecting I/O to offline device
[  414.246268] sd 10:0:0:0: rejecting I/O to offline device
[  414.246276] sd 10:0:0:0: rejecting I/O to offline device
[  414.246285] sd 10:0:0:0: rejecting I/O to offline device
[  414.246294] sd 10:0:0:0: rejecting I/O to offline device
[  414.246303] sd 10:0:0:0: rejecting I/O to offline device
[  414.246311] sd 10:0:0:0: rejecting I/O to offline device
[  414.246320] sd 10:0:0:0: rejecting I/O to offline device
[  414.246329] sd 10:0:0:0: rejecting I/O to offline device
[  414.246338] sd 10:0:0:0: rejecting I/O to offline device
[  414.246347] sd 10:0:0:0: rejecting I/O to offline device
[  414.246356] sd 10:0:0:0: rejecting I/O to offline device
[  414.246365] sd 10:0:0:0: rejecting I/O to offline device
[  414.246374] sd 10:0:0:0: rejecting I/O to offline device
[  414.246384] sd 10:0:0:0: rejecting I/O to offline device
[  414.246394] sd 10:0:0:0: rejecting I/O to offline device
[  414.246402] sd 10:0:0:0: rejecting I/O to offline device
[  414.246411] sd 10:0:0:0: rejecting I/O to offline device
[  414.246419] sd 10:0:0:0: rejecting I/O to offline device
[  414.246428] sd 10:0:0:0: rejecting I/O to offline device
[  414.246437] sd 10:0:0:0: rejecting I/O to offline device
[  414.246446] sd 10:0:0:0: rejecting I/O to offline device
[  414.246454] sd 10:0:0:0: rejecting I/O to offline device
[  414.246463] sd 10:0:0:0: rejecting I/O to offline device
[  414.246472] sd 10:0:0:0: rejecting I/O to offline device
[  414.246481] sd 10:0:0:0: rejecting I/O to offline device
[  414.246490] sd 10:0:0:0: rejecting I/O to offline device
[  414.246506] sd 10:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  414.246508] end_request: I/O error, dev sdd, sector 123688
[  414.246515] sd 10:0:0:0: rejecting I/O to offline device
[  414.246617] sd 10:0:0:0: rejecting I/O to offline device
[  414.246626] sd 10:0:0:0: rejecting I/O to offline device
[  414.246634] sd 10:0:0:0: rejecting I/O to offline device
[  414.246642] sd 10:0:0:0: rejecting I/O to offline device
[  414.246744] sd 10:0:0:0: rejecting I/O to offline device
[  414.246752] sd 10:0:0:0: rejecting I/O to offline device
[  414.246759] sd 10:0:0:0: rejecting I/O to offline device
[  414.246767] sd 10:0:0:0: rejecting I/O to offline device
[  414.246872] sd 10:0:0:0: rejecting I/O to offline device
[  414.246880] sd 10:0:0:0: rejecting I/O to offline device
[  414.246887] sd 10:0:0:0: rejecting I/O to offline device
[  414.246895] sd 10:0:0:0: rejecting I/O to offline device
[  414.247715] sd 10:0:0:0: rejecting I/O to offline device
[  414.247720] sd 10:0:0:0: rejecting I/O to offline device
[  414.247722] __ratelimit: 13 callbacks suppressed
[  414.247724] Buffer I/O error on device sdd1, logical block 1
[  414.247725] lost page write due to I/O error on sdd1
[  414.247727] sd 10:0:0:0: rejecting I/O to offline device
[  414.247729] Buffer I/O error on device sdd1, logical block 8
[  414.247730] lost page write due to I/O error on sdd1
[  414.247732] Buffer I/O error on device sdd1, logical block 9
[  414.247733] lost page write due to I/O error on sdd1
[  414.247735] Buffer I/O error on device sdd1, logical block 10
[  414.247736] lost page write due to I/O error on sdd1
[  414.247738] Buffer I/O error on device sdd1, logical block 11
[  414.247739] lost page write due to I/O error on sdd1
[  414.247740] Buffer I/O error on device sdd1, logical block 12
[  414.247742] lost page write due to I/O error on sdd1
[  414.247743] Buffer I/O error on device sdd1, logical block 13
[  414.247744] lost page write due to I/O error on sdd1
[  414.247746] Buffer I/O error on device sdd1, logical block 14
[  414.247747] lost page write due to I/O error on sdd1
[  414.247749] Buffer I/O error on device sdd1, logical block 15
[  414.247750] lost page write due to I/O error on sdd1
[  414.247752] sd 10:0:0:0: rejecting I/O to offline device
[  414.247753] Buffer I/O error on device sdd1, logical block 245
[  414.247755] lost page write due to I/O error on sdd1
[  414.247776] sd 10:0:0:0: rejecting I/O to offline device
[  414.247783] sd 10:0:0:0: rejecting I/O to offline device
[  414.247786] sd 10:0:0:0: rejecting I/O to offline device
[  414.268586] FAT: FAT read failed (blocknr 15)
[  414.268630] FAT: FAT read failed (blocknr 1)
[  414.270687] FAT: unable to read inode block for updating (i_pos 7827)
[  414.270705] FAT: unable to read inode block for updating (i_pos 7827)
[  414.274990] FAT: FAT read failed (blocknr 15)
[  414.275019] FAT: FAT read failed (blocknr 1)
[  414.275029] FAT: unable to read inode block for updating (i_pos 7827)
[  414.277539] FAT: Directory bread(block 489) failed
[  414.277545] FAT: Directory bread(block 490) failed
[  414.277549] FAT: Directory bread(block 491) failed
[  414.277553] FAT: Directory bread(block 492) failed
[  414.277557] FAT: Directory bread(block 493) failed
[  414.277560] FAT: Directory bread(block 494) failed
[  414.277564] FAT: Directory bread(block 495) failed
[  414.277576] FAT: Directory bread(block 496) failed
[  414.277580] FAT: Directory bread(block 497) failed
[  414.277584] FAT: Directory bread(block 498) failed
[  414.277587] FAT: Directory bread(block 499) failed
[  414.277591] FAT: Directory bread(block 500) failed
[  414.277595] FAT: Directory bread(block 501) failed
[  414.277598] FAT: Directory bread(block 502) failed
[  414.277602] FAT: Directory bread(block 503) failed
[  414.277608] FAT: Directory bread(block 504) failed
[  414.277611] FAT: Directory bread(block 505) failed
[  414.277615] FAT: Directory bread(block 506) failed
[  414.277619] FAT: Directory bread(block 507) failed
[  414.277623] FAT: Directory bread(block 508) failed
[  414.277627] FAT: Directory bread(block 509) failed
[  414.277630] FAT: Directory bread(block 510) failed
[  414.277634] FAT: Directory bread(block 511) failed
[  414.277639] FAT: Directory bread(block 512) failed
[  414.277643] FAT: Directory bread(block 513) failed
[  414.277647] FAT: Directory bread(block 514) failed
[  414.277651] FAT: Directory bread(block 515) failed
[  414.277654] FAT: Directory bread(block 516) failed
[  414.277658] FAT: Directory bread(block 517) failed
[  414.277662] FAT: Directory bread(block 518) failed
[  414.277665] FAT: Directory bread(block 519) failed
[  414.277672] FAT: Directory bread(block 520) failed
[  414.277685] FAT: Directory bread(block 489) failed
[  414.277689] FAT: Directory bread(block 490) failed
[  414.277693] FAT: Directory bread(block 491) failed
[  414.277697] FAT: Directory bread(block 492) failed
[  414.277700] FAT: Directory bread(block 493) failed
[  414.277704] FAT: Directory bread(block 494) failed
[  414.277708] FAT: Directory bread(block 495) failed
[  414.277712] FAT: Directory bread(block 496) failed
[  414.277715] FAT: Directory bread(block 497) failed
[  414.277719] FAT: Directory bread(block 498) failed
[  414.277723] FAT: Directory bread(block 499) failed
[  414.277726] FAT: Directory bread(block 500) failed
[  414.277730] FAT: Directory bread(block 501) failed
[  414.277734] FAT: Directory bread(block 502) failed
[  414.277737] FAT: Directory bread(block 503) failed
[  414.277741] FAT: Directory bread(block 504) failed
[  414.277745] FAT: Directory bread(block 505) failed
[  414.277748] FAT: Directory bread(block 506) failed
[  414.277752] FAT: Directory bread(block 507) failed
[  414.277756] FAT: Directory bread(block 508) failed
[  414.277759] FAT: Directory bread(block 509) failed
[  414.277763] FAT: Directory bread(block 510) failed
[  414.277766] FAT: Directory bread(block 511) failed
[  414.277770] FAT: Directory bread(block 512) failed
[  414.277774] FAT: Directory bread(block 513) failed
[  414.277777] FAT: Directory bread(block 514) failed
[  414.277781] FAT: Directory bread(block 515) failed
[  414.277785] FAT: Directory bread(block 516) failed
[  414.277792] FAT: Directory bread(block 517) failed
[  414.277796] FAT: Directory bread(block 518) failed
[  414.277800] FAT: Directory bread(block 519) failed
[  414.277803] FAT: Directory bread(block 520) failed
[  414.400519] usb 1-6: new high speed USB device using ehci_hcd and address 10
[  414.534187] usb 1-6: configuration #1 chosen from 1 choice
[  414.536105] scsi11 : SCSI emulation for USB Mass Storage devices
[  414.536307] usb-storage: device found at 10
[  414.536309] usb-storage: waiting for device to settle before scanning
[  419.536177] usb-storage: device scan complete
```

i cannot agree with the idea that is a  hardware problem, because i was using the same usb stick with intrepid (i had it working with sudo modprobe - ehci_hcd), and it worked relatively fine (at usb 1.0 speed)

So, any other ideas ??

---

