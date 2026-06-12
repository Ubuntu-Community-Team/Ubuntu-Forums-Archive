---
title: "Issue with a peripheral incompatibility(?)"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by NainNain on 2007-11-15
Hi,

I have recently bought a USB Wireless LAN stick.
I run into trouble since it is connected to one of my USB ports. I really don't know where this comes from!

Here is the thing :
I also have an external hard drive (NTFS format) and a Logitech webcam.

When Ubuntu (7.04) starts up, everything is running well.
But...
After some time (not always the same, usually between 30 and 90 minutes), all the usb peripherals are crashing down. They are actually still detected, but I can't use them anymore (even if I unplug then plug them again).

First I thought it was some kind of power option that was setting my usb ports in sleep mode. So I have turned off most of the power management options of Ubuntu.
But still the problem is there. One weird thing is that this happens sometimes even while the peripherals are being used!

Here is the last log report when this bug occured :

```
/var/log$ sudo grep -r "01:37:04" .
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.466893] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0_scsi_generic').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.642613] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4CA40D4CA0FEC').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.643542] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.644431] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.645319] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.646143] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0').
./debug:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.647041] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E').
./syslog:Nov 13 01:37:04 NainNain kernel: [ 3356.489300] usb 4-2: USB disconnect, address 3
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.466893] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0_scsi_generic').
./syslog:Nov 13 01:37:04 NainNain hald[4548]: forcibly attempting to lazy unmount /dev/sda1 as enclosing drive was disconnected
./syslog:Nov 13 01:37:04 NainNain ntfs-3g[5220]: Unmounting /dev/sda1 (Data)
./syslog:Nov 13 01:37:04 NainNain hald: unmounted /dev/sda1 from '/media/Data' on behalf of uid 0
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.642613] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4CA40D4CA0FEC').
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.643542] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0').
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.644431] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host').
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.645319] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw').
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.646143] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0').
./syslog:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.647041] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E').
./syslog:Nov 13 01:37:04 NainNain kernel: [ 3356.784995] usb 4-2: new high speed USB device using ehci_hcd and address 5
./auth.log:Nov 13 07:20:15 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r 01:37:04 .
./messages:Nov 13 01:37:04 NainNain kernel: [ 3356.489300] usb 4-2: USB disconnect, address 3
./messages:Nov 13 01:37:04 NainNain kernel: [ 3356.784995] usb 4-2: new high speed USB device using ehci_hcd and address 5
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.466893] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0_scsi_generic').
./daemon.log:Nov 13 01:37:04 NainNain hald[4548]: forcibly attempting to lazy unmount /dev/sda1 as enclosing drive was disconnected
./daemon.log:Nov 13 01:37:04 NainNain ntfs-3g[5220]: Unmounting /dev/sda1 (Data)
./daemon.log:Nov 13 01:37:04 NainNain hald: unmounted /dev/sda1 from '/media/Data' on behalf of uid 0
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.642613] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4CA40D4CA0FEC').
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.643542] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_device_lun0').
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.644431] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host').
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.645319] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw').
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.646143] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0').
./daemon.log:Nov 13 01:37:04 NainNain NetworkManager: <debug info>^I[1194914224.647041] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E').
./kern.log:Nov 13 01:37:04 NainNain kernel: [ 3356.489300] usb 4-2: USB disconnect, address 3
./kern.log:Nov 13 01:37:04 NainNain kernel: [ 3356.784995] usb 4-2: new high speed USB device using ehci_hcd and address 5
```

Note : The crash doesn't happen when I leave unplugged either the WiFi stick or the External drive. The drivers I am using for the WiFi stick are RT73 (serialmonkey) as the chipset is from RaLink (but the drivers are from april 07 I think, maybe I should try with the last one?)
Any other ideas? I'm running out of solutions...
Thanks for your help.

---

### Post by NainNain on 2007-11-15
Here a report from today...
Again, the same thing

```

/var/log$ sudo cat debug
Nov 16 01:17:37 NainNain NetworkManager: <debug info>^I[1195172257.696078] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E'). 
Nov 16 01:17:37 NainNain NetworkManager: <debug info>^I[1195172257.905321] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0'). 
Nov 16 01:17:37 NainNain NetworkManager: <debug info>^I[1195172257.974561] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host'). 
Nov 16 01:17:38 NainNain NetworkManager: <debug info>^I[1195172258.027676] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw'). 
Nov 16 01:17:38 NainNain kernel: [22416.973286] usb-storage: device found at 4
Nov 16 01:17:38 NainNain kernel: [22416.973290] usb-storage: waiting for device to settle before scanning
Nov 16 01:17:43 NainNain kernel: [22421.969478] usb-storage: device scan complete
Nov 16 01:17:48 NainNain kernel: [22427.129012] sda: Mode Sense: 33 00 00 00
Nov 16 01:17:48 NainNain kernel: [22427.134150] sda: Mode Sense: 33 00 00 00
Nov 16 01:17:48 NainNain NetworkManager: <debug info>^I[1195172268.271964] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0'). 
Nov 16 01:17:48 NainNain NetworkManager: <debug info>^I[1195172268.321662] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 16 01:17:48 NainNain NetworkManager: <debug info>^I[1195172268.611481] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
Nov 16 01:17:48 NainNain NetworkManager: <debug info>^I[1195172268.709389] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4CA40D4CA0FEC'). 
Nov 16 01:26:36 NainNain NetworkManager: <debug info>^I[1195172796.662360] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.838005] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68D4CA40D4CA0FEC'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.838142] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.838185] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.838223] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.841093] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0'). 
Nov 16 01:26:37 NainNain NetworkManager: <debug info>^I[1195172797.844111] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E'). 
Nov 16 01:26:38 NainNain NetworkManager: <debug info>^I[1195172798.133109] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
Nov 16 01:32:37 NainNain kernel: [    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
Nov 16 01:32:37 NainNain kernel: [    0.000000] On node 0 totalpages: 262128
Nov 16 01:32:37 NainNain kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 16 01:32:37 NainNain kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 16 01:32:37 NainNain kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 16 01:32:37 NainNain kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov 16 01:32:38 NainNain kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov 16 01:32:38 NainNain kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Nov 16 01:32:38 NainNain kernel: [    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: RSDP (v000 KM400                                 ) @ 0x000f79f0
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: RSDT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: FADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: MADT (v001 KM400  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff78c0
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: DSDT (v001 KM400  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 16 01:32:38 NainNain kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 16 01:32:38 NainNain kernel: [   14.791684] mapped APIC to ffffd000 (fee00000)
Nov 16 01:32:38 NainNain kernel: [   14.791686] mapped IOAPIC to ffffc000 (fec00000)
Nov 16 01:32:38 NainNain kernel: [   14.907956] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
Nov 16 01:32:38 NainNain kernel: [   14.907972] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
Nov 16 01:32:38 NainNain kernel: [   15.598395] PCI: Probing PCI hardware (bus 00)
Nov 16 01:32:38 NainNain kernel: [   15.599184] Boot video device is 0000:01:00.0
Nov 16 01:32:38 NainNain kernel: [   15.599258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 16 01:32:38 NainNain kernel: [   15.659254] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov 16 01:32:38 NainNain kernel: [   18.479801] ieee1394: Initialized config rom entry `ip1394'
Nov 16 01:32:38 NainNain kernel: [   18.629303] libata version 2.20 loaded.
Nov 16 01:32:38 NainNain kernel: [   18.979184] Probing IDE interface ide0...
Nov 16 01:32:38 NainNain kernel: [   19.766714] Probing IDE interface ide1...
Nov 16 01:32:38 NainNain kernel: [   19.823388] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000d610000e219]
Nov 16 01:32:38 NainNain kernel: [   21.145234] usb-storage: device found at 3
Nov 16 01:32:38 NainNain kernel: [   21.145236] usb-storage: waiting for device to settle before scanning
Nov 16 01:32:38 NainNain kernel: [   21.942566] swsusp: Resume From Partition 3:69
Nov 16 01:32:38 NainNain kernel: [   21.942568] PM: Checking swsusp image.
Nov 16 01:32:38 NainNain kernel: [   21.950014] PM: Resume from disk failed.
Nov 16 01:32:38 NainNain kernel: [   26.138165] usb-storage: device scan complete
Nov 16 01:32:38 NainNain kernel: [   26.148372] sda: Mode Sense: 33 00 00 00
Nov 16 01:32:38 NainNain kernel: [   26.150120] sda: Mode Sense: 33 00 00 00
Nov 16 01:32:38 NainNain kernel: [   38.858917] irda_init()
Nov 16 01:32:38 NainNain kernel: [   40.165171] PCI: Setting latency timer of device 0000:00:11.6 to 64
Nov 16 01:32:38 NainNain kernel: [   40.697907] PCI: Setting latency timer of device 0000:00:11.5 to 64
Nov 16 01:32:47 NainNain kernel: [   56.410609] rausb0: no IPv6 routers present

```

```
/var/log$ sudo grep -r "01:32:47" .
./debug:Nov 16 01:32:47 NainNain kernel: [   56.410609] rausb0: no IPv6 routers present
./syslog:Nov 16 01:32:47 NainNain anacron[4981]: Anacron 2.3 started on 2007-11-16
./syslog:Nov 16 01:32:47 NainNain anacron[4981]: Will run job `cron.daily' in 5 min.
./syslog:Nov 16 01:32:47 NainNain anacron[4981]: Jobs will be executed sequentially
./syslog:Nov 16 01:32:47 NainNain /usr/sbin/cron[5008]: (CRON) INFO (pidfile fd = 3)
./syslog:Nov 16 01:32:47 NainNain /usr/sbin/cron[5009]: (CRON) STARTUP (fork ok)
./syslog:Nov 16 01:32:47 NainNain /usr/sbin/cron[5009]: (CRON) INFO (Running @reboot jobs)
./syslog:Nov 16 01:32:47 NainNain kernel: [   56.410609] rausb0: no IPv6 routers present
./auth.log:Nov 16 01:45:14 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r 01:32:47 .
./kern.log:Nov 16 01:32:47 NainNain kernel: [   56.410609] rausb0: no IPv6 routers present
achateig@NainNain:/var/log$ sudo grep -r "01:26:38" .
./debug:Nov 16 01:26:38 NainNain NetworkManager: <debug info>^I[1195172798.133109] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
./syslog:Nov 16 01:26:38 NainNain NetworkManager: <debug info>^I[1195172798.133109] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
./auth.log:Nov 16 01:45:26 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r 01:26:38 .
./daemon.log:Nov 16 01:26:38 NainNain NetworkManager: <debug info>^I[1195172798.133109] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 

```

Any ideas?
Thanks

---

### Post by NainNain on 2007-11-20
Hello...
I still have this random unmount which is really annoying...
I have moved my hard drive from the NTFS to the FAT32 format, thinking that it was because of the NTFS -3g module, but still the problem is there...
Any ideas?? Am I really the only one having this issue? :(
Thanks a lot

---

### Post by NainNain on 2007-11-21
Even after updating my libHAL, the problem is still here... again...

```
$ sudo grep -r "Nov 21 22:49:" .
Password:
./debug:Nov 21 22:49:30 NainNain NetworkManager: <debug info>^I[1195681770.957383] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.752376] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4743_39E1'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.755297] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.757273] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.759084] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.760996] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.762817] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
./debug:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.764837] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host'). 
./syslog:Nov 21 22:49:07 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
./syslog:Nov 21 22:49:15 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
./syslog:Nov 21 22:49:26 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
./syslog:Nov 21 22:49:30 NainNain kernel: [  906.204265] usb 4-2: USB disconnect, address 3
./syslog:Nov 21 22:49:30 NainNain kernel: [  906.204570] Buffer I/O error on device sda1, logical block 2626198
./syslog:Nov 21 22:49:30 NainNain kernel: [  906.204575] lost page write due to I/O error on sda1
./syslog:Nov 21 22:49:30 NainNain NetworkManager: <debug info>^I[1195681770.957383] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
./syslog:Nov 21 22:49:31 NainNain hald[4552]: forcibly attempting to lazy unmount /dev/sda1 as enclosing drive was disconnected
./syslog:Nov 21 22:49:31 NainNain kernel: [  906.464013] usb 4-2: new high speed USB device using ehci_hcd and address 5
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.752376] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4743_39E1'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.755297] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.757273] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.759084] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.760996] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.762817] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
./syslog:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.764837] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host'). 
./syslog:Nov 21 22:49:31 NainNain kernel: [  907.004277] scsi 0:0:0:0: rejecting I/O to dead device
./syslog:Nov 21 22:49:31 NainNain kernel: [  907.004372] FAT: unable to read inode block for updating (i_pos 42019172)
./syslog:Nov 21 22:49:38 NainNain dhclient: No DHCPOFFERS received.
./syslog:Nov 21 22:49:38 NainNain dhclient: No working leases in persistent database - sleeping.
./auth.log:Nov 21 22:49:48 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r Nov 21 22:49 .
./auth.log:Nov 21 23:02:31 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r Nov 21 22:49:0 .
./auth.log:Nov 21 23:22:48 NainNain sudo: achateig : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -r Nov 21 22:49: .
./messages:Nov 21 22:49:30 NainNain kernel: [  906.204265] usb 4-2: USB disconnect, address 3
./messages:Nov 21 22:49:30 NainNain kernel: [  906.204575] lost page write due to I/O error on sda1
./messages:Nov 21 22:49:31 NainNain kernel: [  906.464013] usb 4-2: new high speed USB device using ehci_hcd and address 5
./daemon.log:Nov 21 22:49:07 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
./daemon.log:Nov 21 22:49:15 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
./daemon.log:Nov 21 22:49:26 NainNain dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
./daemon.log:Nov 21 22:49:30 NainNain NetworkManager: <debug info>^I[1195681770.957383] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
./daemon.log:Nov 21 22:49:31 NainNain hald[4552]: forcibly attempting to lazy unmount /dev/sda1 as enclosing drive was disconnected
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.752376] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_4743_39E1'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.755297] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host_scsi_device_lun0'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.757273] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_usbraw'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.759084] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.760996] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.762817] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_MAXTOR_S_TM3250820A_DEF10985591E_0_0'). 
./daemon.log:Nov 21 22:49:31 NainNain NetworkManager: <debug info>^I[1195681771.764837] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4b4_6830_DEF10985591E_if0_scsi_host'). 
./daemon.log:Nov 21 22:49:38 NainNain dhclient: No DHCPOFFERS received.
./daemon.log:Nov 21 22:49:38 NainNain dhclient: No working leases in persistent database - sleeping.
./kern.log:Nov 21 22:49:30 NainNain kernel: [  906.204265] usb 4-2: USB disconnect, address 3
./kern.log:Nov 21 22:49:30 NainNain kernel: [  906.204570] Buffer I/O error on device sda1, logical block 2626198
./kern.log:Nov 21 22:49:30 NainNain kernel: [  906.204575] lost page write due to I/O error on sda1
./kern.log:Nov 21 22:49:31 NainNain kernel: [  906.464013] usb 4-2: new high speed USB device using ehci_hcd and address 5
./kern.log:Nov 21 22:49:31 NainNain kernel: [  907.004277] scsi 0:0:0:0: rejecting I/O to dead device
./kern.log:Nov 21 22:49:31 NainNain kernel: [  907.004372] FAT: unable to read inode block for updating (i_pos 42019172)
```

Am I really the only one having this kind of weird stuff?

---

