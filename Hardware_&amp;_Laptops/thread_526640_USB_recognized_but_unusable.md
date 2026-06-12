---
title: "USB recognized but unusable"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by hmss27 on 2007-08-15
I just started using Ubuntu and I am not able to use any USB devices at all.  I have tried a mouse,  usb stick, camera, ipod... I am sure you get the point.

I read through several websites and I have not seen any answers however I did find a few things to try... here is what i know.

root@tom-desktop:~# lspci | grep USB
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

root@tom-desktop:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

These commands were inputted while several usb devices were connected.  As you can see I am getting no device specific feedback which leads me to believe I have a problem.  I had a similar unsolved problem in Mandriva which caused me to try Ubuntu due to the better support structure.  Any assistance is appreciated.

---

### Post by jamesjtucker on 2007-08-15
Try this:
Before connecting the device, run 'tail -f /var/log/syslog'

Connect your device. you should see something like:
```

Aug 15 18:39:04 serenity kernel: [26750.661806] usb-storage: device scan complete
Aug 15 18:39:05 serenity kernel: [26751.851187] scsi 11:0:0:0: Direct-Access     Motorola K1               2.31 PQ: 0 ANSI: 2
Aug 15 18:39:06 serenity kernel: [26752.213357] SCSI device sdb: 3970049 512-byte hdwr sectors (2033 MB)
Aug 15 18:39:06 serenity kernel: [26752.216349] sdb: Write Protect is off
Aug 15 18:39:06 serenity kernel: [26752.216355] sdb: Mode Sense: 0b 00 00 08
Aug 15 18:39:06 serenity kernel: [26752.216360] sdb: assuming drive cache: write through
Aug 15 18:39:06 serenity kernel: [26752.231317] SCSI device sdb: 3970049 512-byte hdwr sectors (2033 MB)
Aug 15 18:39:06 serenity kernel: [26752.234306] sdb: Write Protect is off
Aug 15 18:39:06 serenity kernel: [26752.234311] sdb: Mode Sense: 0b 00 00 08
Aug 15 18:39:06 serenity kernel: [26752.234314] sdb: assuming drive cache: write through
Aug 15 18:39:06 serenity kernel: [26752.234318]  sdb: sdb1
Aug 15 18:39:06 serenity kernel: [26752.602543] sd 11:0:0:0: Attached scsi removable disk sdb
Aug 15 18:39:06 serenity kernel: [26752.602602] sd 11:0:0:0: Attached scsi generic sg2 type 0
Aug 15 18:39:06 serenity NetworkManager: <debug info>^I[1187217546.763846] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_22b8_4810_35942500119564_if0_scsi_host').
Aug 15 18:39:06 serenity NetworkManager: <debug info>^I[1187217546.767064] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_22b8_4810_35942500119564_if0_scsi_host_scsi_device_lun0').
Aug 15 18:39:06 serenity NetworkManager: <debug info>^I[1187217546.768912] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_22b8_4810_35942500119564_if0_scsi_host_scsi_device_lun0_scsi_generic').
Aug 15 18:39:07 serenity NetworkManager: <debug info>^I[1187217547.451993] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Motorola_K1_35942500119564_0_0').
Aug 15 18:39:08 serenity NetworkManager: <debug info>^I[1187217548.555727] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3133_3666').
Aug 15 18:39:09 serenity hald: mounted /dev/sdb1 on behalf of uid 1000

```

If not, it should give some fairly informative errors. It may be detecting things properly, but not automounting the drives, etc.

---

### Post by hmss27 on 2007-08-15
First let me thank you for such a prompt response:  I disconnected the devices and this is what i got

tom@tom-desktop:~$ tail -f /var/log/syslog
Aug 15 18:43:21 tom-desktop gconfd (root-8596): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 15 18:43:21 tom-desktop gconfd (root-8596): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 15 18:43:51 tom-desktop gconfd (root-8596): GConf server is not in use, shutting down.
Aug 15 18:43:51 tom-desktop gconfd (root-8596): Exiting
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): SIGHUP received, reloading all databases
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): Resolved address "xml:readwrite:/home/tom/.gconf" to a writable configuration source at position 1
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 15 18:44:17 tom-desktop gconfd (tom-5366): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

upon reconnecting

tom@tom-desktop:~$ tail -f /var/log/syslog
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): starting (version 2.18.0.1), pid 5381 user 'tom'
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): Resolved address "xml:readwrite:/home/tom/.gconf" to a writable configuration source at position 1
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 15 19:16:06 tom-desktop gconfd (tom-5381): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 15 19:16:10 tom-desktop gconfd (tom-5381): Resolved address "xml:readwrite:/home/tom/.gconf" to a writable configuration source at position 0
Aug 15 19:16:14 tom-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Aug 15 19:16:14 tom-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

  
I dont know what this means but perhaps it will help.

---

### Post by hmss27 on 2007-08-16
Can anyone tell me how to fix this problem.  I feel like this could be the problem preventing me from using my usb.

```
[    4.751915] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.751922] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[COLOR="Red"][    4.752332] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.752381] ehci_hcd 0000:00:1d.7: debug port 1
[    4.752391] PCI: cache line size of 128 is not supported by device 0000:00:1d.7[/COLOR]
[    4.752405] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xffa80800
[    4.756301] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.758843] usb usb1: configuration #1 chosen from 1 choice
[    4.758900] hub 1-0:1.0: USB hub found
[    4.758914] hub 1-0:1.0: 8 ports detected
[    5.026004] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0c:f1:c8:
```

---

