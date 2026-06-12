---
title: "Pen Drive only detected if plugged in at boot time"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by deepsky on 2007-06-19
Hi,

I have just received a new Corsair Flash Voyager 16GB pen drive. Unfortunately, I have problems with it under Ubuntu 7.04 (i386).
I am running the following kernel:
2.6.20-15-generic

One problem is that the pen drive seems to be recognized only if I boot my machine with the device plugged in.
If I plug out the device and plug it back in, I see some error messages in /var/log/syslog and the pen drive is not recognized. Here is the output of /var/log/syslog after unplugging and re-plugging the pen drive after booting the machine:

<PLUGGING OUT...>
Jun 19 10:20:04 localhost hald[4991]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.183793] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun 19 10:20:04 localhost kernel: [  116.844000] usb 4-2: USB disconnect, address 2
Jun 19 10:20:04 localhost hald: unmounted /dev/sdb1 from '/media/CORSAIR' on behalf of uid 0
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.262821] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_0000_060C').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.264508] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074_if0_scsi_host_scsi_device_lun0').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.266088] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074_usbraw').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.267383] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074_if0').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.268725] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.270109] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA99000000006074_if0_scsi_host').
Jun 19 10:20:04 localhost NetworkManager: <debug info>^I[1182244804.280299] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Corsair_Flash_Voyager_AA99000000006074_0_0').

<PLUGGING IN>
Jun 19 10:20:15 localhost kernel: [  128.388000] usb 4-2: new high speed USB device using ehci_hcd and address 4
Jun 19 10:20:17 localhost kernel: [  130.408000] usb 4-2: device descriptor read/64, error -32
Jun 19 10:20:17 localhost kernel: [  130.624000] usb 4-2: device descriptor read/64, error -32
Jun 19 10:20:18 localhost kernel: [  130.840000] usb 4-2: new high speed USB device using ehci_hcd and address 5
Jun 19 10:20:18 localhost kernel: [  130.952000] usb 4-2: device descriptor read/64, error -32
Jun 19 10:20:18 localhost kernel: [  131.168000] usb 4-2: device descriptor read/64, error -32
Jun 19 10:20:18 localhost kernel: [  131.384000] usb 4-2: new high speed USB device using ehci_hcd and address 6
Jun 19 10:20:19 localhost kernel: [  131.792000] usb 4-2: device not accepting address 6, error -32


Note also that even when booting the machine with the pen drive plugged in, the writing speed is terrible. It took me 1h30 to write 6GB of data...
Here are the lines in /var/log/syslog where the pen drive was recognized at boot time:

Jun 19 10:22:09 localhost kernel: [    6.160000] usb 2-2: new low speed USB device using uhci_hcd and address 2
Jun 19 10:22:09 localhost kernel: [    6.336000] usb 2-2: configuration #1 chosen from 1 choice
Jun 19 10:22:09 localhost kernel: [    6.336000] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 19 10:22:09 localhost kernel: [    6.336000] usb-storage: device found at 2
Jun 19 10:22:09 localhost kernel: [    6.336000] usb-storage: waiting for device to settle before scanning
Jun 19 10:22:09 localhost kernel: [    6.336000] usbcore: registered new interface driver usb-storage
Jun 19 10:22:09 localhost kernel: [    6.336000] USB Mass Storage support registered.
Jun 19 10:22:09 localhost kernel: [    6.876000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000016df10]
Jun 19 10:22:09 localhost kernel: [   11.336000] usb-storage: device scan complete
Jun 19 10:22:09 localhost kernel: [   11.336000] scsi 2:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
Jun 19 10:22:09 localhost kernel: [   11.336000] SCSI device sdb: 31719424 512-byte hdwr sectors (16240 MB)
Jun 19 10:22:09 localhost kernel: [   11.336000] sdb: Write Protect is off
Jun 19 10:22:09 localhost kernel: [   11.336000] sdb: Mode Sense: 43 00 00 00
Jun 19 10:22:09 localhost kernel: [   11.336000] sdb: assuming drive cache: write through
Jun 19 10:22:09 localhost kernel: [   11.340000] SCSI device sdb: 31719424 512-byte hdwr sectors (16240 MB)
Jun 19 10:22:09 localhost kernel: [   11.340000] sdb: Write Protect is off
Jun 19 10:22:09 localhost kernel: [   11.340000] sdb: Mode Sense: 43 00 00 00
Jun 19 10:22:09 localhost kernel: [   11.340000] sdb: assuming drive cache: write through
Jun 19 10:22:09 localhost kernel: [   11.340000]  sdb: sdb1
Jun 19 10:22:09 localhost kernel: [   11.340000] sd 2:0:0:0: Attached scsi removable disk sdb




Thanks for your help!

---

### Post by brussel on 2007-07-01
I have the same model and the same problem. I've been searching everywhere and I see many people have the same problem but nobody has answers.

---

