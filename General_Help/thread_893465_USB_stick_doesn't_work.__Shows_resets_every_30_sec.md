---
title: "USB stick doesn't work.  Shows resets every 30 seconds in logs."
date: 2008-08-18
forum: General Help
---

### Post by miatawnt2b on 2008-08-18
I am trying to use a 2Gb USB memory stick on my Dell laptop running a new install of Hardy.  The stick won't mount and in /var/log/messages I am seeing the following:

```
Aug 18 10:05:18 miata kernel: [ 5502.977888] usb 4-1: new high speed USB device using ehci_hcd and address 4
Aug 18 10:05:18 miata kernel: [ 5503.111000] usb 4-1: configuration #1 chosen from 1 choice
Aug 18 10:05:18 miata kernel: [ 1649.124471] usbcore: registered new interface driver libusual
Aug 18 10:05:18 miata kernel: [ 1649.165265] Initializing USB Mass Storage driver...
Aug 18 10:05:18 miata kernel: [ 1649.166541] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 18 10:05:18 miata kernel: [ 1649.168477] usbcore: registered new interface driver usb-storage
Aug 18 10:05:18 miata kernel: [ 1649.168483] USB Mass Storage support registered.
Aug 18 10:05:23 miata kernel: [ 5509.694633] scsi 2:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
Aug 18 10:05:23 miata kernel: [ 5509.705543] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Aug 18 10:05:23 miata kernel: [ 5509.713389] sd 2:0:0:0: [sdb] Write Protect is off
Aug 18 10:05:23 miata kernel: [ 5509.716067] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Aug 18 10:05:23 miata kernel: [ 5509.716821] sd 2:0:0:0: [sdb] Write Protect is off
Aug 18 10:05:23 miata kernel: [ 5509.716846]  sdb: sdb1
Aug 18 10:05:23 miata kernel: [ 5509.719058] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 18 10:05:23 miata kernel: [ 5509.719167] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 18 10:05:53 miata kernel: [ 5548.562948] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:06:24 miata kernel: [ 5587.519068] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:06:54 miata kernel: [ 5622.603549] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:07:24 miata kernel: [ 5688.451523] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:07:54 miata kernel: [ 1722.565104] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:08:25 miata kernel: [ 5795.574216] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:08:25 miata kernel: [ 5795.706970] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 18 10:08:25 miata kernel: [ 5795.706986] end_request: I/O error, dev sdb, sector 2039680

```

and from syslog:

```
ug 18 10:05:18 miata kernel: [ 5502.977888] usb 4-1: new high speed USB device using ehci_hcd and address 4
Aug 18 10:05:18 miata kernel: [ 5503.111000] usb 4-1: configuration #1 chosen from 1 choice
Aug 18 10:05:18 miata NetworkManager: <debug> [1219068318.369843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_204_6025_201459002627D203'). 
Aug 18 10:05:18 miata kernel: [ 1649.124471] usbcore: registered new interface driver libusual
Aug 18 10:05:18 miata NetworkManager: <debug> [1219068318.560052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_204_6025_201459002627D203_if0'). 
Aug 18 10:05:18 miata kernel: [ 1649.165265] Initializing USB Mass Storage driver...
Aug 18 10:05:18 miata kernel: [ 1649.166541] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 18 10:05:18 miata kernel: [ 1649.168477] usbcore: registered new interface driver usb-storage
Aug 18 10:05:18 miata kernel: [ 1649.168483] USB Mass Storage support registered.
Aug 18 10:05:18 miata kernel: [ 1649.168838] usb-storage: device found at 4
Aug 18 10:05:18 miata kernel: [ 1649.168841] usb-storage: waiting for device to settle before scanning
Aug 18 10:05:23 miata kernel: [ 5509.693627] usb-storage: device scan complete
Aug 18 10:05:23 miata kernel: [ 5509.694633] scsi 2:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
Aug 18 10:05:23 miata kernel: [ 5509.705543] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Aug 18 10:05:23 miata kernel: [ 5509.713389] sd 2:0:0:0: [sdb] Write Protect is off
Aug 18 10:05:23 miata kernel: [ 5509.713400] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Aug 18 10:05:23 miata kernel: [ 5509.713407] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 10:05:23 miata kernel: [ 5509.716067] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Aug 18 10:05:23 miata kernel: [ 5509.716821] sd 2:0:0:0: [sdb] Write Protect is off
Aug 18 10:05:23 miata kernel: [ 5509.716831] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Aug 18 10:05:23 miata kernel: [ 5509.716838] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 10:05:23 miata kernel: [ 5509.716846]  sdb: sdb1
Aug 18 10:05:23 miata kernel: [ 5509.719058] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 18 10:05:23 miata kernel: [ 5509.719167] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 18 10:05:23 miata NetworkManager: <debug> [1219068323.695366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_204_6025_201459002627D203_if0_scsi_host'). 
Aug 18 10:05:23 miata NetworkManager: <debug> [1219068323.698965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_204_6025_201459002627D203_if0_scsi_host_scsi_device_lun0'). 
Aug 18 10:05:23 miata NetworkManager: <debug> [1219068323.721195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_204_6025_201459002627D203_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 18 10:05:53 miata kernel: [ 5548.562948] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:06:24 miata kernel: [ 5587.519068] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:06:54 miata kernel: [ 5622.603549] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:07:24 miata kernel: [ 5688.451523] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:07:54 miata kernel: [ 1722.565104] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:08:25 miata kernel: [ 5795.574216] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:08:25 miata kernel: [ 5795.706970] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 18 10:08:25 miata kernel: [ 5795.706986] end_request: I/O error, dev sdb, sector 2039680
Aug 18 10:08:25 miata kernel: [ 5795.706996] Buffer I/O error on device sdb, logical block 254960
Aug 18 10:08:55 miata kernel: [ 5831.739105] usb 4-1: reset high speed USB device using ehci_hcd and address 4
Aug 18 10:09:10 miata kernel: [ 5850.520924] usb 4-1: device descriptor read/64, error -110
Aug 18 10:09:25 miata kernel: [ 5866.641871] usb 4-1: device descriptor read/64, error -110
Aug 18 10:09:25 miata kernel: [ 1758.031697] usb 4-1: reset high speed USB device using ehci_hcd and address 4
```

I have seen this issue as well on previous versions as well.  Can someone help me get this working?

Thanks,
-J

---

### Post by miatawnt2b on 2008-08-19
bump

---

### Post by miatawnt2b on 2008-08-25
bumping this one up again.  I really need a solution.
-J

---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.:popcorn:
I hope this help someone.

---

### Post by insub2 on 2008-10-02
Thanks marioitalo!

---

### Post by miatawnt2b on 2008-10-03
I had high hopes for this but nope... didn't change anything.

```
Oct  3 10:24:28 miata kernel: [  334.753203] usb 4-1: new high speed USB device using ehci_hcd and address 3
Oct  3 10:24:29 miata kernel: [  334.886421] usb 4-1: configuration #1 chosen from 1 choice
Oct  3 10:24:29 miata kernel: [  100.459470] usbcore: registered new interface driver libusual
Oct  3 10:24:29 miata kernel: [  100.499413] Initializing USB Mass Storage driver...
Oct  3 10:24:29 miata kernel: [  100.500624] scsi2 : SCSI emulation for USB Mass Storage devices
Oct  3 10:24:29 miata kernel: [  100.502579] usbcore: registered new interface driver usb-storage
Oct  3 10:24:29 miata kernel: [  100.502585] USB Mass Storage support registered.
Oct  3 10:24:34 miata kernel: [  341.885150] scsi 2:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
Oct  3 10:24:34 miata kernel: [  341.899736] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Oct  3 10:24:34 miata kernel: [  341.900508] sd 2:0:0:0: [sdb] Write Protect is off
Oct  3 10:24:34 miata kernel: [  341.903252] sd 2:0:0:0: [sdb] 2039808 512-byte hardware sectors (1044 MB)
Oct  3 10:24:34 miata kernel: [  341.904004] sd 2:0:0:0: [sdb] Write Protect is off
Oct  3 10:24:34 miata kernel: [  341.904029]  sdb: sdb1
Oct  3 10:24:34 miata kernel: [  341.905867] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Oct  3 10:24:34 miata kernel: [  341.905962] sd 2:0:0:0: Attached scsi generic sg2 type 0
Oct  3 10:25:04 miata kernel: [  380.491227] usb 4-1: reset high speed USB device using ehci_hcd and address 3
Oct  3 10:25:34 miata kernel: [  414.899426] usb 4-1: reset high speed USB device using ehci_hcd and address 3
Oct  3 10:25:44 miata kernel: [  424.926118] usb 4-1: USB disconnect, address 3
Oct  3 10:25:44 miata kernel: [  424.926827] scsi 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Oct  3 10:25:44 miata kernel: [  424.926840] end_request: I/O error, dev sdb, sector 2039680
```

---

