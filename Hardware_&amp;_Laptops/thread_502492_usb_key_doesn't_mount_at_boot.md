---
title: "usb key doesn't mount at boot"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by bozo_the_grey on 2007-07-16
Hi,
my usb key is not always mounted at boot. An External USD drive is always mounted, instead (maybe because sometimes I plug the key to a different port while the drive is always plugged to the same?).

System is:
Linux acer-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I noticed a memory error when booting, just before the ubuntu splash screen. Don't know if it's related to a problem with the usb ports.

I attach some output from gvm as suggested here:
[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)


And the syslog that seems to be saying something:
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.723546] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_28X_075B1D90BE6E_0_0').

Here is the complete syslog:

Jul 15 20:56:50 acer-laptop syslogd 1.4.1#20ubuntu4: restart.
Jul 15 20:56:51 acer-laptop anacron[5400]: Job `cron.daily' terminated
Jul 15 20:56:51 acer-laptop anacron[5400]: Normal exit (1 job run)
Jul 15 21:02:28 acer-laptop kernel: [ 804.100000] usb 4-2: USB disconnect, address 3
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.103063] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_if0_scsi_host_sc si_device_lun0_scsi_generic').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.103476] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_if0_scsi_host_sc si_device_lun0').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.103789] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_if0_scsi_host').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.104097] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_usbraw').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.104456] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_11DC_D102').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.104764] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_if0').
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.105089] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E').
Jul 15 21:02:28 acer-laptop usbmgr[5095]: "scsi_mod" was unloaded
Jul 15 21:02:28 acer-laptop usbmgr[5095]: "sd_mod" was unloaded
Jul 15 21:02:28 acer-laptop usbmgr[5095]: "usb-storage" was unloaded
Jul 15 21:02:28 acer-laptop NetworkManager: <debug info>^I[1184529748.723546] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_28X_075B1D90BE6E_0_0').
Jul 15 21:02:33 acer-laptop hald: unmounted /dev/sda1 from '/media/BACKUP_' on behalf of uid 1000
Jul 15 21:02:41 acer-laptop kernel: [ 817.496000] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
Jul 15 21:02:41 acer-laptop hald: mounted /dev/sda1 on behalf of uid 1000
Jul 15 21:02:41 acer-laptop kernel: [ 817.968000] NTFS volume version 3.1.
Jul 15 21:03:15 acer-laptop kernel: [ 851.212000] usb 4-2: new high speed USB device using ehci_hcd and address 5
Jul 15 21:03:15 acer-laptop kernel: [ 851.348000] usb 4-2: configuration #1 chosen from 1 choice
Jul 15 21:03:15 acer-laptop kernel: [ 851.348000] scsi2 : SCSI emulation for USB Mass Storage devices
Jul 15 21:03:15 acer-laptop kernel: [ 851.348000] usb-storage: device found at 5
Jul 15 21:03:15 acer-laptop kernel: [ 851.348000] usb-storage: waiting for device to settle before scanning
Jul 15 21:03:15 acer-laptop NetworkManager: <debug info>^I[1184529795.418124] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E').
Jul 15 21:03:15 acer-laptop NetworkManager: <debug info>^I[1184529795.555909] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_if0').
Jul 15 21:03:15 acer-laptop NetworkManager: <debug info>^I[1184529795.556944] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1a00_075B1D90BE6E_usbraw').
Jul 15 21:03:15 acer-laptop usbmgr[5095]: vendor:0x13fe product:0x1a00
Jul 15 21:03:15 acer-laptop usbmgr[5095]: class:0x8 subclass:0x6 protocol:0x50
Jul 15 21:03:16 acer-laptop usbmgr[5095]: USB device is matched the configuration
Jul 15 21:03:16 acer-laptop usbmgr[5095]: "scsi_mod" was loaded
Jul 15 21:03:16 acer-laptop usbmgr[5095]: "sd_mod" was loaded
Jul 15 21:03:16 acer-laptop usbmgr[5095]: "usb-storage" was loaded
Jul 15 21:03:20 acer-laptop kernel: [ 856.348000] usb-storage: device scan complete

Thanks

Stefano

---

