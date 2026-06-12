---
title: "Issues with particular USB devices not working"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Abdi110 on 2007-07-10
In the past few weeks (not too sure what I did to initiate this issue), some USB devices stopped working. Namely my Sandisk SD/USB card, some USB hard drives and my USB hub. Some times the device will work early on after boot for a few minutes, then stop. On my Sandisk card, the read/write light blinks on/off quickly when it gets into the state (instead of being solid on). The same goes with if I plug in my USB mouse through my USB hub.

Here's an excerpt from dmesg | grep usb...

```
[    9.234055] usbcore: registered new interface driver usbfs
[    9.234120] usbcore: registered new interface driver hub
[    9.234176] usbcore: registered new device driver usb
[    9.236802] PM: Adding info for usb:usb1
[    9.236868] PM: Adding info for No Bus:usbdev1.1_ep00
[    9.236886] usb usb1: configuration #1 chosen from 1 choice
[    9.236929] PM: Adding info for usb:1-0:1.0
[    9.343956] PM: Adding info for No Bus:usbdev1.1_ep81
[    9.344002] PM: Adding info for No Bus:usbdev1.1
[    9.344879] PM: Adding info for usb:usb2
[    9.344930] PM: Adding info for No Bus:usbdev2.1_ep00
[    9.344948] usb usb2: configuration #1 chosen from 1 choice
[    9.345013] PM: Adding info for usb:2-0:1.0
[    9.449017] PM: Adding info for No Bus:usbdev2.1_ep81
[    9.449064] PM: Adding info for No Bus:usbdev2.1
[    9.449937] PM: Adding info for usb:usb3
[    9.449995] PM: Adding info for No Bus:usbdev3.1_ep00
[    9.450013] usb usb3: configuration #1 chosen from 1 choice
[    9.450057] PM: Adding info for usb:3-0:1.0
[    9.552996] PM: Adding info for No Bus:usbdev3.1_ep81
[    9.553040] PM: Adding info for No Bus:usbdev3.1
[    9.558662] PM: Adding info for usb:usb4
[    9.558717] PM: Adding info for No Bus:usbdev4.1_ep00
[    9.558735] usb usb4: configuration #1 chosen from 1 choice
[    9.558779] PM: Adding info for usb:4-0:1.0
[    5.876000] PM: Adding info for No Bus:usbdev4.1_ep81
[    5.876000] PM: Adding info for No Bus:usbdev4.1
[    7.300000] usb 4-4: new high speed USB device using ehci_hcd and address 7
[    8.728000] usb 4-4: new high speed USB device using ehci_hcd and address 14
[    9.968000] usb 4-4: new high speed USB device using ehci_hcd and address 20
[   11.208000] usb 4-4: new high speed USB device using ehci_hcd and address 26
[   11.508000] usb 4-4: new high speed USB device using ehci_hcd and address 27
[   12.936000] usb 4-4: new high speed USB device using ehci_hcd and address 34
[   15.116000] usb 4-4: new high speed USB device using ehci_hcd and address 45
[   17.484000] usb 4-4: new high speed USB device using ehci_hcd and address 57
[   18.536000] usb 4-4: new high speed USB device using ehci_hcd and address 62
[   22.220000] usb 4-4: new high speed USB device using ehci_hcd and address 81
[   22.520000] usb 4-4: new high speed USB device using ehci_hcd and address 82
[   23.008000] usb 4-4: new high speed USB device using ehci_hcd and address 84
[   23.920000] usb 4-4: new high speed USB device using ehci_hcd and address 85
[   24.220000] usb 4-4: new high speed USB device using ehci_hcd and address 86

Cut most of that out as I'm sure you get the idea.

[ 1384.280000] usb 4-4: new high speed USB device using ehci_hcd and address 71
[ 1389.328000] usb 4-4: new high speed USB device using ehci_hcd and address 94
[ 1396.772000] usb 4-4: new high speed USB device using ehci_hcd and address 7
[ 1397.824000] usb 4-4: new high speed USB device using ehci_hcd and address 12
[ 1400.192000] usb 4-4: new high speed USB device using ehci_hcd and address 24
[ 1400.680000] usb 4-4: new high speed USB device using ehci_hcd and address 26
```

If I just leave a "broken" device plugged in, it'll continue spewing out the new high speed messages. Some times if I just get into bash before logging into Gnome, I'll see stuff like this pop up in the terminal...

```
[  1617.148000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[  1617.148000] hub 4-0:1.0: hub_port_status failed (err = -32)
[  1617.148000] hub 4-0:1.0: Cannot enable port 4. Maybe the USB cable is bad?
```

I just updated my kernel to 2.6.22 and that didn't seem to fix it. I also have to drop into bash before logging into Gnome and restart dbus in order for gnome-power-manager to work correctly with my ThinkPad T41, as Synaptic wont let me force an older version that isn't so broken. Either way with dbus USB still doesn't work.

I did drop into my Windows boot for a second and did notice that USB works fine, so I'm pretty sure it's not my hardware.

After doing a few searches through the forums, the only issues I could find even slightly related to my problem sounded more like mount issues then USB just flat out not working. I would really appreciate some help as getting access to my SD card again would be rather nice. Thanks in advance.

---

### Post by Abdi110 on 2007-07-10
Here's what lsusb displays...

```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

And when I've got my usb SD card plugged in, lsmod | grep usb...

```
usbcore               137736  3 ehci_hcd,uhci_hcd
```

Also booting into the default kernel, 2.6.20-15, doesn't make this work.

---

