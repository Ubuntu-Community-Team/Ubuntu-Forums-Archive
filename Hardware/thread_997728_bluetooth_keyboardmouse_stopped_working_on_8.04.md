---
title: "bluetooth keyboard/mouse stopped working on 8.04"
date: 2008-11-30
forum: Hardware
---

### Post by phylae on 2008-11-30
My bluetooth mouse suddenly stopped working. This happens to me a few times a week, and all I need to do is run `sudo /etc/init.d/bluetooth restart` and then it starts working again. This time it didn't. I tried running that command several times. I also tried rebooting.

After poking around online I found a few tutorials that suggested that I edit this file: /etc/default/bluetooth
That didn't help so I put it back.

After another restart, my bluetooth keyword wouldn't work either.

When I go to "bluetooth preferences" | "adaptors", the "mode of operation" is greyed out, so I can't follow the instructions posted here: [https://help.ubuntu.com/community/BluetoothInputDevices?action=show&redirect=BluetoothMouse](https://help.ubuntu.com/community/BluetoothInputDevices?action=show&redirect=BluetoothMouse)

I have been googling like crazy and I don't know what to do next!!

My laptop is a Dell XPS M1330. I have Ubuntu 8.04.

From what I can tell, these commands might help solve the problem:

```

$ modprobe -l *blue*

/lib/modules/2.6.24-19-generic/kernel/net/bluetooth/bluetooth.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/bluetooth/bluecard_cs.ko

```


```

$ dpkg -l|grep blue

ii  bluez-audio                                3.26-0ubuntu6                                        Bluetooth audio support
ii  bluez-cups                                 3.26-0ubuntu6                                        Bluetooth printer driver for CUPS
ii  bluez-gnome                                0.25-0ubuntu1                                        Bluetooth utilities for GNOME
ii  bluez-utils                                3.26-0ubuntu6                                        Bluetooth tools and daemons
ii  gnome-bluetooth                            0.11.0-0ubuntu1                                      GNOME Bluetooth tools.
ii  libbluetooth2                              3.29-0ubuntu1                                        Library to use the BlueZ Linux Bluetooth stack

```

```

$ grep blue /var/log/syslog

Nov 30 00:17:57 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:20:23 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:20:59 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.RemoveDevice()
Nov 30 00:21:04 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.RemoveDevice()
Nov 30 00:37:58 laptop hcid[8162]: Unregister path: /org/bluez/hci0
Nov 30 00:37:58 laptop hcid[8162]: Unregister path: /org/bluez
Nov 30 00:37:58 laptop audio[8170]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:37:59 laptop input[22580]: Registered input manager path:/org/bluez/input
Nov 30 00:38:02 laptop audio[22582]: Registered manager path:/org/bluez/audio
Nov 30 00:38:02 laptop hcid[22571]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:38:02 laptop hcid[22571]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:38:06 laptop input[22580]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:38:06 laptop audio[22582]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:40:32 laptop input[6715]: Registered input manager path:/org/bluez/input
Nov 30 00:40:35 laptop audio[6730]: Registered manager path:/org/bluez/audio
Nov 30 00:41:04 laptop hcid[6693]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:41:04 laptop hcid[6693]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:41:50 laptop input[6715]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:41:50 laptop audio[6730]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:46:07 laptop hcid[6693]: Unregister path: /org/bluez/hci0
Nov 30 00:46:07 laptop hcid[6693]: Unregister path: /org/bluez
Nov 30 00:46:07 laptop audio[6730]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:46:08 laptop input[9742]: Registered input manager path:/org/bluez/input
Nov 30 00:46:08 laptop hcid[9736]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:46:08 laptop hcid[9736]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:46:11 laptop audio[9744]: Registered manager path:/org/bluez/audio
Nov 30 00:57:46 laptop hcid[9736]: Unregister path: /org/bluez/hci0
Nov 30 00:57:46 laptop hcid[9736]: Unregister path: /org/bluez
Nov 30 00:57:46 laptop audio[9744]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:57:57 laptop input[14747]: Registered input manager path:/org/bluez/input
Nov 30 00:57:57 laptop hcid[14744]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:57:57 laptop hcid[14744]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:58:00 laptop audio[14748]: Registered manager path:/org/bluez/audio
Nov 30 00:58:30 laptop hcid[14744]: Unregister path: /org/bluez/hci0
Nov 30 00:58:30 laptop hcid[14744]: Unregister path: /org/bluez
Nov 30 00:58:30 laptop audio[14748]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:58:31 laptop input[14983]: Registered input manager path:/org/bluez/input
Nov 30 00:58:31 laptop hcid[14977]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:58:31 laptop hcid[14977]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:58:34 laptop audio[14985]: Registered manager path:/org/bluez/audio
Nov 30 01:00:13 laptop input[14983]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 01:00:13 laptop audio[14985]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 01:03:24 laptop hcid[14977]: Unregister path: /org/bluez/hci0
Nov 30 01:03:24 laptop hcid[14977]: Unregister path: /org/bluez
Nov 30 01:03:24 laptop audio[14985]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 01:03:42 laptop input[17743]: Registered input manager path:/org/bluez/input
Nov 30 01:03:42 laptop hcid[17740]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 01:03:42 laptop hcid[17740]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 01:03:45 laptop audio[17744]: Registered manager path:/org/bluez/audio
Nov 30 01:04:02 laptop hcid[17740]: Unregister path: /org/bluez/hci0
Nov 30 01:04:02 laptop hcid[17740]: Unregister path: /org/bluez
Nov 30 01:04:02 laptop audio[17744]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 01:04:03 laptop input[17898]: Registered input manager path:/org/bluez/input
Nov 30 01:04:03 laptop hcid[17892]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 01:04:03 laptop hcid[17892]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 01:04:06 laptop audio[17900]: Registered manager path:/org/bluez/audio
Nov 30 01:11:54 laptop input[17898]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 01:11:54 laptop audio[17900]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()

```

```

$ hciconfig -a

hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:60 acl:0 sco:0 events:10 errors:0
	TX bytes:75 acl:0 sco:0 commands:25 errors:0


```


```

$ sudo hciconfig hci0 up

Can't init device hci0: Connection timed out (110)

```


```

$ sudo hcitool scan

Device is not available: No such device

```


```

$ sudo hidd --search

Searching ...

```

```

$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


```


```

$ lsusb

Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000

```

```

$ grep blue /var/log/daemon.log

Nov 26 11:11:59 laptop NetworkManager: <debug> [1227726719.882087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 26 11:12:00 laptop NetworkManager: <debug> [1227726720.437384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 26 11:12:06 laptop NetworkManager: <debug> [1227726726.231083] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 26 11:12:06 laptop NetworkManager: <debug> [1227726726.645035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 26 11:32:14 laptop NetworkManager: <debug> [1227727934.146148] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 26 11:32:14 laptop NetworkManager: <debug> [1227727934.146918] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 26 11:32:16 laptop NetworkManager: <debug> [1227727936.646611] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 26 11:32:16 laptop NetworkManager: <debug> [1227727936.646671] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 26 15:59:00 laptop NetworkManager: <debug> [1227743940.181580] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 26 15:59:00 laptop NetworkManager: <debug> [1227743940.492926] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 26 15:59:02 laptop NetworkManager: <debug> [1227743942.734976] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 26 15:59:03 laptop NetworkManager: <debug> [1227743943.089805] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 26 18:25:25 laptop NetworkManager: <debug> [1227752725.748332] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 26 18:25:25 laptop NetworkManager: <debug> [1227752725.748821] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 26 18:25:27 laptop NetworkManager: <debug> [1227752727.547526] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 26 18:25:27 laptop NetworkManager: <debug> [1227752727.547648] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 26 23:08:12 laptop NetworkManager: <debug> [1227769692.503522] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 26 23:08:13 laptop NetworkManager: <debug> [1227769693.291807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 26 23:20:15 laptop NetworkManager: <debug> [1227770415.493478] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 26 23:20:16 laptop NetworkManager: <debug> [1227770416.001653] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 05:15:57 laptop NetworkManager: <debug> [1227791757.166821] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 05:15:57 laptop NetworkManager: <debug> [1227791757.168445] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 05:16:00 laptop NetworkManager: <debug> [1227791760.291299] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 05:16:00 laptop NetworkManager: <debug> [1227791760.293410] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 12:16:40 laptop NetworkManager: <debug> [1227817000.507102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 12:16:41 laptop NetworkManager: <debug> [1227817001.105127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 12:16:46 laptop NetworkManager: <debug> [1227817006.894971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 12:16:47 laptop NetworkManager: <debug> [1227817007.313215] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 14:08:59 laptop NetworkManager: <debug> [1227823739.693349] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 14:08:59 laptop NetworkManager: <debug> [1227823739.693556] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 14:09:03 laptop NetworkManager: <debug> [1227823743.441940] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 14:09:03 laptop NetworkManager: <debug> [1227823743.442935] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 14:10:04 laptop NetworkManager: <debug> [1227823804.689091] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 14:10:04 laptop NetworkManager: <debug> [1227823805.000669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 14:16:18 laptop input[6727]: Registered input manager path:/org/bluez/input
Nov 27 14:16:18 laptop input[6727]: Created input device: /org/bluez/input/pointing0
Nov 27 14:16:18 laptop input[6727]: Created input device: /org/bluez/input/keyboard1
Nov 27 14:16:18 laptop audio[6745]: Registered manager path:/org/bluez/audio
Nov 27 14:17:04 laptop NetworkManager: <debug> [1227824224.822127] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 14:17:05 laptop NetworkManager: <debug> [1227824225.312679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 14:17:16 laptop NetworkManager: <debug> [1227824236.287233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 14:17:16 laptop NetworkManager: <debug> [1227824236.650502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 14:17:18 laptop hcid[6717]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 27 14:17:18 laptop hcid[6717]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 27 17:59:56 laptop NetworkManager: <debug> [1227837596.200112] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 17:59:56 laptop NetworkManager: <debug> [1227837596.200244] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 17:59:58 laptop NetworkManager: <debug> [1227837598.699057] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 27 17:59:58 laptop NetworkManager: <debug> [1227837598.700877] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 21:22:26 laptop NetworkManager: <debug> [1227849746.414913] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 27 21:22:26 laptop NetworkManager: <debug> [1227849746.752598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 27 21:22:30 laptop NetworkManager: <debug> [1227849750.257467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 27 21:22:30 laptop NetworkManager: <debug> [1227849750.619675] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 28 02:27:47 laptop NetworkManager: <debug> [1227868067.062606] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 28 02:27:51 laptop NetworkManager: <debug> [1227868071.858236] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 28 02:58:38 laptop NetworkManager: <debug> [1227869918.213591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 28 02:58:38 laptop NetworkManager: <debug> [1227869918.563783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci_0_1_logicaldev_input'). 
Nov 28 03:30:14 laptop input[6794]: Registered input manager path:/org/bluez/input
Nov 28 03:30:14 laptop input[6794]: Created input device: /org/bluez/input/pointing0
Nov 28 03:30:14 laptop input[6794]: Created input device: /org/bluez/input/keyboard1
Nov 28 03:30:15 laptop audio[6805]: Registered manager path:/org/bluez/audio
Nov 28 03:30:45 laptop hcid[6772]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 28 03:30:45 laptop hcid[6772]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 28 16:20:49 laptop input[6659]: Registered input manager path:/org/bluez/input
Nov 28 16:20:49 laptop input[6659]: Created input device: /org/bluez/input/pointing0
Nov 28 16:20:49 laptop input[6659]: Created input device: /org/bluez/input/keyboard1
Nov 28 16:20:49 laptop audio[6667]: Registered manager path:/org/bluez/audio
Nov 28 16:24:51 laptop input[6672]: Registered input manager path:/org/bluez/input
Nov 28 16:24:51 laptop input[6672]: Created input device: /org/bluez/input/pointing0
Nov 28 16:24:51 laptop input[6672]: Created input device: /org/bluez/input/keyboard1
Nov 28 16:24:51 laptop audio[6675]: Registered manager path:/org/bluez/audio
Nov 28 16:28:34 laptop hcid[6661]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 28 16:28:34 laptop hcid[6661]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 28 16:29:49 laptop NetworkManager: <debug> [1227918589.679826] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 28 16:29:50 laptop NetworkManager: <debug> [1227918590.502847] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 28 16:30:40 laptop NetworkManager: <debug> [1227918640.664961] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 28 16:30:41 laptop NetworkManager: <debug> [1227918641.333802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 28 16:30:48 laptop hcid[6661]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 28 16:30:48 laptop hcid[6661]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 28 18:45:06 laptop NetworkManager: <debug> [1227926706.700588] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 28 18:45:06 laptop NetworkManager: <debug> [1227926706.702975] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 28 18:45:08 laptop NetworkManager: <debug> [1227926708.573450] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 28 18:45:08 laptop NetworkManager: <debug> [1227926708.573573] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 28 19:10:43 laptop NetworkManager: <debug> [1227928243.813949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 28 19:10:44 laptop NetworkManager: <debug> [1227928244.183482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 28 19:10:47 laptop NetworkManager: <debug> [1227928247.637589] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 28 19:10:47 laptop NetworkManager: <debug> [1227928247.990890] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 02:29:25 laptop NetworkManager: <debug> [1227954565.241752] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 02:29:29 laptop NetworkManager: <debug> [1227954569.875235] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 02:31:51 laptop NetworkManager: <debug> [1227954711.462528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 02:31:52 laptop NetworkManager: <debug> [1227954712.398396] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 06:09:22 laptop NetworkManager: <debug> [1227967762.207774] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 06:09:26 laptop NetworkManager: <debug> [1227967766.964993] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 06:10:32 laptop NetworkManager: <debug> [1227967832.089760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 06:10:32 laptop NetworkManager: <debug> [1227967832.816458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 07:24:48 laptop NetworkManager: <debug> [1227972288.949503] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 07:24:53 laptop NetworkManager: <debug> [1227972293.746369] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 07:27:45 laptop NetworkManager: <debug> [1227972465.924026] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 07:27:46 laptop NetworkManager: <debug> [1227972466.319582] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 07:31:11 laptop NetworkManager: <debug> [1227972671.258823] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 29 07:31:11 laptop NetworkManager: <debug> [1227972671.261885] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 07:31:14 laptop NetworkManager: <debug> [1227972674.350377] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 07:31:14 laptop NetworkManager: <debug> [1227972674.352620] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 15:16:46 laptop NetworkManager: <debug> [1228000606.273829] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 15:16:46 laptop NetworkManager: <debug> [1228000606.707184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 29 15:17:14 laptop NetworkManager: <debug> [1228000634.369573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 15:17:14 laptop NetworkManager: <debug> [1228000634.775333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 16:21:14 laptop NetworkManager: <debug> [1228004474.132641] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 16:21:18 laptop NetworkManager: <debug> [1228004478.935549] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 16:23:57 laptop NetworkManager: <debug> [1228004637.108523] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 16:23:57 laptop NetworkManager: <debug> [1228004637.508313] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci_0_1_logicaldev_input'). 
Nov 29 22:40:59 laptop NetworkManager: <debug> [1228027259.447575] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 29 22:41:04 laptop NetworkManager: <debug> [1228027264.083591] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 22:41:11 laptop NetworkManager: <debug> [1228027271.213390] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci_0_1_logicaldev_input'). 
Nov 29 22:41:15 laptop NetworkManager: <debug> [1228027275.918864] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 22:44:55 laptop NetworkManager: <debug> [1228027495.288323] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 22:44:55 laptop NetworkManager: <debug> [1228027495.607530] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 29 22:45:34 laptop NetworkManager: <debug> [1228027534.800767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 22:45:35 laptop NetworkManager: <debug> [1228027535.107228] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 23:25:34 laptop hcid[6661]: Unregister path: /org/bluez/hci0
Nov 29 23:25:34 laptop hcid[6661]: Unregister path: /org/bluez
Nov 29 23:25:34 laptop audio[6675]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:25:36 laptop input[3002]: Registered input manager path:/org/bluez/input
Nov 29 23:25:36 laptop hcid[2993]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:25:36 laptop hcid[2993]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:25:36 laptop input[3002]: Created input device: /org/bluez/input/pointing0
Nov 29 23:25:36 laptop input[3002]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:25:41 laptop audio[3003]: Registered manager path:/org/bluez/audio
Nov 29 23:25:42 laptop NetworkManager: <debug> [1228029942.101181] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b_logicaldev_input'). 
Nov 29 23:25:42 laptop NetworkManager: <debug> [1228029942.102487] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:25:42 laptop NetworkManager: <debug> [1228029942.183987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:25:47 laptop hcid[2993]: Unregister path: /org/bluez/hci0
Nov 29 23:25:47 laptop hcid[2993]: Unregister path: /org/bluez
Nov 29 23:25:47 laptop audio[3003]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:25:49 laptop input[3091]: Registered input manager path:/org/bluez/input
Nov 29 23:25:49 laptop input[3091]: Created input device: /org/bluez/input/pointing0
Nov 29 23:25:49 laptop input[3091]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:25:49 laptop hcid[3082]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:25:49 laptop hcid[3082]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:25:54 laptop audio[3092]: Registered manager path:/org/bluez/audio
Nov 29 23:25:57 laptop hcid[3082]: Unregister path: /org/bluez/hci0
Nov 29 23:25:57 laptop hcid[3082]: Unregister path: /org/bluez
Nov 29 23:25:57 laptop audio[3092]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:25:59 laptop input[3173]: Registered input manager path:/org/bluez/input
Nov 29 23:25:59 laptop input[3173]: Created input device: /org/bluez/input/pointing0
Nov 29 23:25:59 laptop input[3173]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:25:59 laptop hcid[3165]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:25:59 laptop hcid[3165]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:26:02 laptop NetworkManager: <debug> [1228029962.206313] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:26:04 laptop audio[3174]: Registered manager path:/org/bluez/audio
Nov 29 23:26:07 laptop NetworkManager: <debug> [1228029967.382333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:26:08 laptop hcid[3165]: Unregister path: /org/bluez/hci0
Nov 29 23:26:08 laptop hcid[3165]: Unregister path: /org/bluez
Nov 29 23:26:08 laptop audio[3174]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:26:10 laptop input[3271]: Registered input manager path:/org/bluez/input
Nov 29 23:26:10 laptop input[3271]: Created input device: /org/bluez/input/pointing0
Nov 29 23:26:10 laptop input[3271]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:26:10 laptop hcid[3247]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:26:11 laptop hcid[3247]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:26:15 laptop audio[3275]: Registered manager path:/org/bluez/audio
Nov 29 23:26:27 laptop NetworkManager: <debug> [1228029987.813382] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:26:35 laptop hcid[3247]: Unregister path: /org/bluez/hci0
Nov 29 23:26:35 laptop hcid[3247]: Unregister path: /org/bluez
Nov 29 23:26:35 laptop audio[3275]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:26:37 laptop input[3455]: Registered input manager path:/org/bluez/input
Nov 29 23:26:37 laptop input[3455]: Created input device: /org/bluez/input/pointing0
Nov 29 23:26:37 laptop input[3455]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:26:37 laptop hcid[3447]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:26:37 laptop hcid[3447]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:26:42 laptop audio[3456]: Registered manager path:/org/bluez/audio
Nov 29 23:26:43 laptop NetworkManager: <debug> [1228030003.200084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:26:47 laptop hcid[3447]: Unregister path: /org/bluez/hci0
Nov 29 23:26:47 laptop hcid[3447]: Unregister path: /org/bluez
Nov 29 23:26:47 laptop audio[3456]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:26:49 laptop input[3540]: Registered input manager path:/org/bluez/input
Nov 29 23:26:49 laptop input[3540]: Created input device: /org/bluez/input/pointing0
Nov 29 23:26:49 laptop input[3540]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:26:49 laptop hcid[3532]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:26:49 laptop hcid[3532]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:26:54 laptop audio[3541]: Registered manager path:/org/bluez/audio
Nov 29 23:26:57 laptop input[3540]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 29 23:26:57 laptop audio[3541]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 29 23:27:02 laptop input[3540]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 29 23:27:03 laptop NetworkManager: <debug> [1228030023.219035] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:27:47 laptop NetworkManager: <debug> [1228030067.909492] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:28:02 laptop hcid[3532]: Unregister path: /org/bluez/hci0
Nov 29 23:28:02 laptop hcid[3532]: Unregister path: /org/bluez
Nov 29 23:28:02 laptop audio[3541]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:28:04 laptop input[3958]: Registered input manager path:/org/bluez/input
Nov 29 23:28:04 laptop input[3958]: Created input device: /org/bluez/input/pointing0
Nov 29 23:28:04 laptop input[3958]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:28:04 laptop hcid[3950]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:28:04 laptop hcid[3950]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:28:08 laptop NetworkManager: <debug> [1228030088.006272] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:28:09 laptop audio[3959]: Registered manager path:/org/bluez/audio
Nov 29 23:32:47 laptop NetworkManager: <debug> [1228030367.371997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:32:57 laptop hcid[3950]: Unregister path: /org/bluez/hci0
Nov 29 23:32:57 laptop hcid[3950]: Unregister path: /org/bluez
Nov 29 23:32:57 laptop audio[3959]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:32:59 laptop input[6001]: Registered input manager path:/org/bluez/input
Nov 29 23:32:59 laptop input[6001]: Created input device: /org/bluez/input/pointing0
Nov 29 23:32:59 laptop input[6001]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:32:59 laptop hcid[5993]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:32:59 laptop hcid[5993]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:33:04 laptop audio[6002]: Registered manager path:/org/bluez/audio
Nov 29 23:33:07 laptop NetworkManager: <debug> [1228030387.445954] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:33:38 laptop NetworkManager: <debug> [1228030418.123012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:33:58 laptop NetworkManager: <debug> [1228030438.252789] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:34:27 laptop NetworkManager: <debug> [1228030467.620598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:34:47 laptop NetworkManager: <debug> [1228030487.628076] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:36:08 laptop NetworkManager: <debug> [1228030568.037850] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:36:28 laptop NetworkManager: <debug> [1228030588.121008] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:40:25 laptop NetworkManager: <debug> [1228030825.470824] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:40:33 laptop hcid[5993]: Unregister path: /org/bluez/hci0
Nov 29 23:40:33 laptop hcid[5993]: Unregister path: /org/bluez
Nov 29 23:40:33 laptop audio[6002]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:40:35 laptop input[9143]: Registered input manager path:/org/bluez/input
Nov 29 23:40:35 laptop input[9143]: Created input device: /org/bluez/input/pointing0
Nov 29 23:40:35 laptop input[9143]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:40:35 laptop hcid[9108]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:40:35 laptop hcid[9108]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:40:40 laptop audio[9144]: Registered manager path:/org/bluez/audio
Nov 29 23:40:45 laptop NetworkManager: <debug> [1228030845.516342] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:40:48 laptop NetworkManager: <debug> [1228030848.202328] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:41:08 laptop NetworkManager: <debug> [1228030868.279577] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:41:53 laptop input[9143]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 29 23:41:53 laptop audio[9144]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 29 23:41:57 laptop input[9143]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 29 23:42:14 laptop NetworkManager: <debug> [1228030934.677508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:42:34 laptop NetworkManager: <debug> [1228030954.700250] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:44:59 laptop hcid[9108]: Unregister path: /org/bluez/hci0
Nov 29 23:44:59 laptop hcid[9108]: Unregister path: /org/bluez
Nov 29 23:45:01 laptop input[10657]: Registered input manager path:/org/bluez/input
Nov 29 23:45:01 laptop input[10657]: Created input device: /org/bluez/input/pointing0
Nov 29 23:45:01 laptop input[10657]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:45:01 laptop hcid[10641]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:45:01 laptop hcid[10641]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:45:03 laptop NetworkManager: <debug> [1228031103.983745] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:45:04 laptop audio[10658]: Registered manager path:/org/bluez/audio
Nov 29 23:45:11 laptop hcid[10641]: Unregister path: /org/bluez/hci0
Nov 29 23:45:11 laptop hcid[10641]: Unregister path: /org/bluez
Nov 29 23:45:11 laptop audio[10658]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:45:13 laptop input[10739]: Registered input manager path:/org/bluez/input
Nov 29 23:45:13 laptop input[10739]: Created input device: /org/bluez/input/pointing0
Nov 29 23:45:13 laptop input[10739]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:45:13 laptop hcid[10730]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:45:13 laptop hcid[10730]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:45:16 laptop audio[10740]: Registered manager path:/org/bluez/audio
Nov 29 23:45:24 laptop NetworkManager: <debug> [1228031124.109532] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:45:40 laptop NetworkManager: <debug> [1228031140.752421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:46:21 laptop NetworkManager: <debug> [1228031181.058008] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:46:33 laptop hcid[10730]: Unregister path: /org/bluez/hci0
Nov 29 23:46:33 laptop hcid[10730]: Unregister path: /org/bluez
Nov 29 23:46:33 laptop audio[10740]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:46:33 laptop NetworkManager: <debug> [1228031193.758698] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a_logicaldev_input'). 
Nov 29 23:46:34 laptop NetworkManager: <debug> [1228031194.673152] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:46:35 laptop input[11270]: Registered input manager path:/org/bluez/input
Nov 29 23:46:35 laptop input[11270]: Created input device: /org/bluez/input/pointing0
Nov 29 23:46:35 laptop input[11270]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:46:35 laptop hcid[11258]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:46:35 laptop hcid[11258]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:46:38 laptop audio[11271]: Registered manager path:/org/bluez/audio
Nov 29 23:46:41 laptop NetworkManager: <debug> [1228031201.076659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:46:45 laptop NetworkManager: <debug> [1228031205.015823] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:47:01 laptop NetworkManager: <debug> [1228031221.152092] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:47:05 laptop NetworkManager: <debug> [1228031225.028318] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:47:06 laptop NetworkManager: <debug> [1228031226.346288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:47:19 laptop NetworkManager: <debug> [1228031239.098732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:47:26 laptop NetworkManager: <debug> [1228031246.433004] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:47:31 laptop NetworkManager: <debug> [1228031251.636865] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:47:39 laptop NetworkManager: <debug> [1228031259.196151] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:47:51 laptop NetworkManager: <debug> [1228031271.670119] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:47:53 laptop NetworkManager: <debug> [1228031273.033102] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:48:13 laptop NetworkManager: <debug> [1228031293.044222] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:48:16 laptop hcid[11258]: Unregister path: /org/bluez/hci0
Nov 29 23:48:16 laptop hcid[11258]: Unregister path: /org/bluez
Nov 29 23:48:16 laptop audio[11271]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:48:18 laptop input[11925]: Registered input manager path:/org/bluez/input
Nov 29 23:48:18 laptop input[11925]: Created input device: /org/bluez/input/pointing0
Nov 29 23:48:18 laptop input[11925]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:48:18 laptop hcid[11915]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:48:18 laptop hcid[11915]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:48:19 laptop NetworkManager: <debug> [1228031299.450738] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:48:21 laptop audio[11926]: Registered manager path:/org/bluez/audio
Nov 29 23:48:23 laptop NetworkManager: <debug> [1228031303.357309] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:48:39 laptop NetworkManager: <debug> [1228031319.437824] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f542a'). 
Nov 29 23:48:43 laptop NetworkManager: <debug> [1228031323.414765] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_7615f971b'). 
Nov 29 23:49:50 laptop hcid[11915]: Unregister path: /org/bluez/hci0
Nov 29 23:49:50 laptop hcid[11915]: Unregister path: /org/bluez
Nov 29 23:49:50 laptop audio[11926]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:49:52 laptop input[12510]: Registered input manager path:/org/bluez/input
Nov 29 23:49:52 laptop input[12510]: Created input device: /org/bluez/input/pointing0
Nov 29 23:49:52 laptop input[12510]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:49:52 laptop hcid[12502]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:49:52 laptop hcid[12502]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:49:55 laptop audio[12511]: Registered manager path:/org/bluez/audio
Nov 29 23:50:10 laptop hcid[12502]: Unregister path: /org/bluez/hci0
Nov 29 23:50:10 laptop hcid[12502]: Unregister path: /org/bluez
Nov 29 23:50:10 laptop audio[12511]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 29 23:50:12 laptop input[12649]: Registered input manager path:/org/bluez/input
Nov 29 23:50:12 laptop input[12649]: Created input device: /org/bluez/input/pointing0
Nov 29 23:50:12 laptop input[12649]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:50:12 laptop hcid[12641]: Default passkey agent (:1.58, /org/bluez/passkey) registered
Nov 29 23:50:12 laptop hcid[12641]: Default authorization agent (:1.58, /org/bluez/auth) registered
Nov 29 23:50:15 laptop audio[12650]: Registered manager path:/org/bluez/audio
Nov 29 23:54:29 laptop input[6726]: Registered input manager path:/org/bluez/input
Nov 29 23:54:29 laptop input[6726]: Created input device: /org/bluez/input/pointing0
Nov 29 23:54:29 laptop input[6726]: Created input device: /org/bluez/input/keyboard1
Nov 29 23:54:32 laptop audio[6741]: Registered manager path:/org/bluez/audio
Nov 29 23:59:57 laptop hcid[6716]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 29 23:59:57 laptop hcid[6716]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:01:18 laptop hcid[6716]: Unregister path: /org/bluez/hci0
Nov 30 00:01:18 laptop hcid[6716]: Unregister path: /org/bluez
Nov 30 00:01:18 laptop audio[6741]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:01:19 laptop input[8168]: Registered input manager path:/org/bluez/input
Nov 30 00:01:19 laptop input[8168]: Created input device: /org/bluez/input/pointing0
Nov 30 00:01:19 laptop input[8168]: Created input device: /org/bluez/input/keyboard1
Nov 30 00:01:19 laptop hcid[8162]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:01:19 laptop hcid[8162]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:01:22 laptop audio[8170]: Registered manager path:/org/bluez/audio
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:02:18 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:02:18 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:02:45 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:02:45 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:17:57 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:17:57 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:20:23 laptop audio[8170]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAdapter()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetAddress()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/pointing0: org.bluez.input.Device.GetName()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAdapter()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetAddress()
Nov 30 00:20:23 laptop input[8168]: /org/bluez/input/keyboard1: org.bluez.input.Device.GetName()
Nov 30 00:20:59 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.RemoveDevice()
Nov 30 00:21:04 laptop input[8168]: /org/bluez/input: org.bluez.input.Manager.RemoveDevice()
Nov 30 00:37:58 laptop hcid[8162]: Unregister path: /org/bluez/hci0
Nov 30 00:37:58 laptop hcid[8162]: Unregister path: /org/bluez
Nov 30 00:37:58 laptop audio[8170]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:37:59 laptop input[22580]: Registered input manager path:/org/bluez/input
Nov 30 00:38:02 laptop audio[22582]: Registered manager path:/org/bluez/audio
Nov 30 00:38:02 laptop hcid[22571]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:38:02 laptop hcid[22571]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:38:06 laptop input[22580]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:38:06 laptop audio[22582]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:40:32 laptop input[6715]: Registered input manager path:/org/bluez/input
Nov 30 00:40:35 laptop audio[6730]: Registered manager path:/org/bluez/audio
Nov 30 00:41:04 laptop hcid[6693]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:41:04 laptop hcid[6693]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:41:50 laptop input[6715]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 00:41:50 laptop audio[6730]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 00:46:07 laptop hcid[6693]: Unregister path: /org/bluez/hci0
Nov 30 00:46:07 laptop hcid[6693]: Unregister path: /org/bluez
Nov 30 00:46:07 laptop audio[6730]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:46:08 laptop input[9742]: Registered input manager path:/org/bluez/input
Nov 30 00:46:08 laptop hcid[9736]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:46:08 laptop hcid[9736]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:46:11 laptop audio[9744]: Registered manager path:/org/bluez/audio
Nov 30 00:57:46 laptop hcid[9736]: Unregister path: /org/bluez/hci0
Nov 30 00:57:46 laptop hcid[9736]: Unregister path: /org/bluez
Nov 30 00:57:46 laptop audio[9744]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:57:57 laptop input[14747]: Registered input manager path:/org/bluez/input
Nov 30 00:57:57 laptop hcid[14744]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:57:57 laptop hcid[14744]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:58:00 laptop audio[14748]: Registered manager path:/org/bluez/audio
Nov 30 00:58:30 laptop hcid[14744]: Unregister path: /org/bluez/hci0
Nov 30 00:58:30 laptop hcid[14744]: Unregister path: /org/bluez
Nov 30 00:58:30 laptop audio[14748]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 00:58:31 laptop input[14983]: Registered input manager path:/org/bluez/input
Nov 30 00:58:31 laptop hcid[14977]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 00:58:31 laptop hcid[14977]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 00:58:34 laptop audio[14985]: Registered manager path:/org/bluez/audio
Nov 30 01:00:13 laptop input[14983]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 01:00:13 laptop audio[14985]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
Nov 30 01:03:24 laptop hcid[14977]: Unregister path: /org/bluez/hci0
Nov 30 01:03:24 laptop hcid[14977]: Unregister path: /org/bluez
Nov 30 01:03:24 laptop audio[14985]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 01:03:42 laptop input[17743]: Registered input manager path:/org/bluez/input
Nov 30 01:03:42 laptop hcid[17740]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 01:03:42 laptop hcid[17740]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 01:03:45 laptop audio[17744]: Registered manager path:/org/bluez/audio
Nov 30 01:04:02 laptop hcid[17740]: Unregister path: /org/bluez/hci0
Nov 30 01:04:02 laptop hcid[17740]: Unregister path: /org/bluez
Nov 30 01:04:02 laptop audio[17744]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Nov 30 01:04:03 laptop input[17898]: Registered input manager path:/org/bluez/input
Nov 30 01:04:03 laptop hcid[17892]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Nov 30 01:04:03 laptop hcid[17892]: Default authorization agent (:1.19, /org/bluez/auth) registered
Nov 30 01:04:06 laptop audio[17900]: Registered manager path:/org/bluez/audio
Nov 30 01:11:54 laptop input[17898]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
Nov 30 01:11:54 laptop audio[17900]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()

```

Thanks!

---

### Post by phylae on 2008-11-30
> **phylae said:**
> 
When I go to "bluetooth preferences" | "adaptors", the "mode of operation" is greyed out, so I can't follow the instructions posted here: [https://help.ubuntu.com/community/BluetoothInputDevices?action=show&redirect=BluetoothMouse](https://help.ubuntu.com/community/BluetoothInputDevices?action=show&redirect=BluetoothMouse)


Well after a few more restarts "mode of operation" was no longer greyed out. I was able to connect my mouse with those instructions. They didn't work for my keyboard, but I was able to connect that with hcitool --search and hidd --connect

If anyone has any comments or insights on why this might have happened, I would appreciate it.

Thanks

---

