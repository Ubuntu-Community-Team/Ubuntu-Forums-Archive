---
title: "USB goes away after Gutsy upgrade"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by mnewell on 2007-11-13
I have a Dell D600 laptop that I'm using as mostly a server.  It's running Ubuntu Gutsy Gibbon workstation version.   It has a broken screen so I leave its lid closed and have an external monitor and USB keyboard and mouse connected.  In addition I have 3 external USB drives that I share out to my network via SAMBA.  The laptop itself is plugged into a docking station and all USB devices are plugged into the docking station USB ports.  

The keyboard and mouse are plugged directly into the docking station ports.  The external drives are connected to a powered external USB 2.0 hub, which is then connected to the docking station.  I had to do this arrangement because the docking station only has 3 ports.  :-(

Under Fiesty this worked Just Fine(tm).

Since upgrading to Gutsy I notice that after a while my file shares disappear (sorry that I cannot quantify "a while" better; since I don't use the shares daily I don't have specific timings).  When I connect to the console the keyboard and mouse are dead and the screen is blank; no banging on keys or moving mouse helps.  I can still SSH into the box; when I do I find that all services are up and running as expected however ALL USB devices are gone.  There are no "/dev/sdx" devices (other than the internal hard disks) and, as noted above, the keyboard and mouse are dead.

I can reboot and everything comes back just fine.  Until the next time they disappear...

I notice in the kernel log I see messages indicating that at some point "usb 4-6.4" disconnects all the devices, then tries to reset.  This is met with hub_port_status failed (err = -71).  For a minute or so the system keeps resetting USB devices - and finding the keyaboard -  then eventually stops; after that there are no more kernel log messages relating to the USB.

I have tried power cycling each USB device, plugging and unplugging them, pushing the "start" buttons on the drives, etc.  I've also tried moving the devices to the laptop's internal USB ports.  Nothing recovers the USB ports except rebooting.  I have also tried opening the lid and typing on the internal keyboard and messing with the internal track pad to no effect.

Anyone with ideas?  I've searched a number of postings and Google but so far have come up dry.  Detailed log messages are included below...  Note that prior to this block of messages the only mention of USB ports in the logs is 3 days earlier when I did the last reboot...  I did not add, remove, or change ports on any of the attached devices during this time.

Thanks,

Mike

------------------------------------------- Detailed log messages ------------------------------------------------
Nov 12 06:19:45 alexandria kernel: [199424.620000] usb 4-6.4: USB disconnect, address 5
Nov 12 06:19:45 alexandria kernel: [199424.620000] usb 4-6.4.1: USB disconnect, address 6
Nov 12 06:19:45 alexandria kernel: [199424.624000] usb 4-6.4.3: USB disconnect, address 11
Nov 12 06:19:45 alexandria kernel: [199424.624000] usb 4-6.4.4: USB disconnect, address 13
Nov 12 06:19:45 alexandria kernel: [199424.624000] usb 4-6.4.5: USB disconnect, address 14
Nov 12 06:19:54 alexandria kernel: [199433.276000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:19:55 alexandria kernel: [199434.388000] hub 4-6:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
Nov 12 06:20:07 alexandria kernel: [199446.128000] hub 4-6:1.0: hub_port_status failed (err = -71)
Nov 12 06:20:07 alexandria kernel: [199446.128000] hub 4-6:1.0: connect-debounce failed, port 4 disabled
Nov 12 06:20:07 alexandria kernel: [199447.004000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:20:13 alexandria kernel: [199452.628000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:20:47 alexandria kernel: [199486.200000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:21:09 alexandria kernel: [199508.808000] hub 4-6:1.0: hub_port_status failed (err = -71)
Nov 12 06:21:09 alexandria kernel: [199509.068000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:21:57 alexandria kernel: [199556.212000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:21:57 alexandria kernel: [199556.764000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:23:32 alexandria kernel: [199651.404000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:23:52 alexandria kernel: [199671.672000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:23:53 alexandria kernel: [199672.228000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 4
Nov 12 06:23:53 alexandria kernel: [199672.512000] usb 4-6.3: device firmware changed
Nov 12 06:23:53 alexandria kernel: [199672.512000] usb 4-6: clear tt 3 (8040) error -32
Nov 12 06:23:53 alexandria kernel: [199672.512000] usb 4-6.3: USB disconnect, address 4
Nov 12 06:23:53 alexandria kernel: [199672.584000] usb 4-6.3: new low speed USB device using ehci_hcd and address 95
Nov 12 06:23:53 alexandria kernel: [199672.692000] usb 4-6.3: configuration #1 chosen from 1 choice
Nov 12 06:23:53 alexandria kernel: [199672.700000] input: Chicony  USB Keyboard as /class/input/input11
Nov 12 06:23:53 alexandria kernel: [199672.700000] input: USB HID v1.00 Keyboard [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:23:53 alexandria kernel: [199672.712000] input: Chicony  USB Keyboard as /class/input/input12
Nov 12 06:23:53 alexandria kernel: [199672.716000] input,hiddev96: USB HID v1.00 Device [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:23:59 alexandria kernel: [199678.888000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:24:02 alexandria kernel: [199681.588000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:25:26 alexandria kernel: [199765.584000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:25:52 alexandria kernel: [199791.348000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:26:03 alexandria kernel: [199802.796000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:26:19 alexandria kernel: [199818.884000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:27:02 alexandria kernel: [199862.080000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:27:07 alexandria kernel: [199866.920000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:27:30 alexandria kernel: [199889.124000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:28:05 alexandria kernel: [199924.660000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: input irq status -75 received
Nov 12 06:29:23 alexandria kernel: [200002.268000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 95
Nov 12 06:29:23 alexandria kernel: [200002.556000] usb 4-6.3: failed to restore interface 1 altsetting 0 (error=-71)
Nov 12 06:29:23 alexandria kernel: [200002.556000] usb 4-6: clear tt 3 (05f0) error -32
Nov 12 06:29:23 alexandria kernel: [200002.556000] usb 4-6.3: USB disconnect, address 95
Nov 12 06:29:23 alexandria kernel: [200002.632000] usb 4-6.3: new low speed USB device using ehci_hcd and address 96
Nov 12 06:29:23 alexandria kernel: [200002.740000] usb 4-6.3: configuration #1 chosen from 1 choice
Nov 12 06:29:23 alexandria kernel: [200002.748000] input: Chicony  USB Keyboard as /class/input/input13
Nov 12 06:29:23 alexandria kernel: [200002.748000] input: USB HID v1.00 Keyboard [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:29:23 alexandria kernel: [200002.764000] input: Chicony  USB Keyboard as /class/input/input14
Nov 12 06:29:23 alexandria kernel: [200002.764000] input,hiddev96: USB HID v1.00 Device [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:29:59 alexandria kernel: [200038.584000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 96
Nov 12 06:29:59 alexandria kernel: [200038.864000] usb 4-6.3: device descriptor read/all, error -32
Nov 12 06:30:00 alexandria kernel: [200039.124000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 96
Nov 12 06:30:00 alexandria kernel: [200039.404000] usb 4-6.3: device descriptor read/all, error -32
Nov 12 06:30:00 alexandria kernel: [200039.664000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 96
Nov 12 06:30:00 alexandria kernel: [200039.684000] usb 4-6.3: device descriptor read/8, error -32
Nov 12 06:30:00 alexandria kernel: [200039.804000] usb 4-6.3: device descriptor read/8, error -32
Nov 12 06:30:01 alexandria kernel: [200040.168000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 96
Nov 12 06:30:01 alexandria kernel: [200040.188000] usb 4-6.3: device descriptor read/8, error -32
Nov 12 06:30:01 alexandria kernel: [200040.308000] usb 4-6.3: device descriptor read/8, error -32
Nov 12 06:30:01 alexandria kernel: [200040.412000] usb 4-6: clear tt 3 (8600) error -32
Nov 12 06:30:01 alexandria kernel: [200040.412000] usb 4-6.3: USB disconnect, address 96
Nov 12 06:30:01 alexandria kernel: [200040.484000] usb 4-6.3: new low speed USB device using ehci_hcd and address 97
Nov 12 06:30:01 alexandria kernel: [200040.592000] usb 4-6.3: configuration #1 chosen from 1 choice
Nov 12 06:30:01 alexandria kernel: [200040.600000] input: Chicony  USB Keyboard as /class/input/input15
Nov 12 06:30:01 alexandria kernel: [200040.600000] input: USB HID v1.00 Keyboard [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:30:01 alexandria kernel: [200040.616000] input: Chicony  USB Keyboard as /class/input/input16
Nov 12 06:30:01 alexandria kernel: [200040.616000] input,hiddev96: USB HID v1.00 Device [Chicony  USB Keyboard] on usb-0000:00:1d.7-6.3
Nov 12 06:30:28 alexandria kernel: [200067.724000] usb 4-6.3: reset low speed USB device using ehci_hcd and address 97
Nov 12 06:30:28 alexandria kernel: [200068.012000] usb 4-6.3: failed to restore interface 1 altsetting 0 (error=-71)
Nov 12 06:30:28 alexandria kernel: [200068.012000] usb 4-6: clear tt 3 (0610) error -32
Nov 12 06:30:28 alexandria kernel: [200068.012000] usb 4-6.3: USB disconnect, address 97
Nov 12 06:30:28 alexandria kernel: [200068.088000] usb 4-6.3: new low speed USB device using ehci_hcd and address 98
Nov 12 06:30:29 alexandria kernel: [200068.160000] usb 4-6.3: device descriptor read/64, error -71
Nov 12 06:30:29 alexandria kernel: [200068.336000] usb 4-6.3: device descriptor read/64, error -71
Nov 12 06:30:29 alexandria kernel: [200068.512000] usb 4-6.3: new low speed USB device using ehci_hcd and address 99
Nov 12 06:30:29 alexandria kernel: [200068.584000] usb 4-6.3: device descriptor read/64, error -71
Nov 12 06:30:29 alexandria kernel: [200068.760000] usb 4-6.3: device descriptor read/64, error -71
Nov 12 06:30:29 alexandria kernel: [200068.936000] usb 4-6.3: new low speed USB device using ehci_hcd and address 100
Nov 12 06:30:30 alexandria kernel: [200069.344000] usb 4-6.3: device not accepting address 100, error -71
Nov 12 06:30:30 alexandria kernel: [200069.416000] usb 4-6.3: new low speed USB device using ehci_hcd and address 101
Nov 12 06:30:30 alexandria kernel: [200069.824000] usb 4-6.3: device not accepting address 101, error -71

---

### Post by mannheim on 2007-11-28
I have had a very similar experience twice in the last week (and never before). I have an external USB hard disk connected directly to my PC, and a keyboard and mouse conneted via a powered usb hub. I have come to work twice to find the keyboard and mouse "dead" and the usb drive in its standby mode. Unplugging the devices and plugging them into other ports has no effect; the little green LEDs on the keyboard don't even flicker. Everything usb-related is dead.

The logs show:

```
Nov 28 09:07:35 pretzel kernel: [167060.448684] usb 2-1: USB disconnect, address 2
Nov 28 09:07:35 pretzel kernel: [167060.448692] usb 2-1.1: USB disconnect, address 4
Nov 28 09:07:35 pretzel kernel: [167060.448696] usb 2-1.1.1: USB disconnect, address 5
Nov 28 09:07:35 pretzel kernel: [167060.449394] usb 2-1.1.3: USB disconnect, address 6
Nov 28 09:07:35 pretzel kernel: [167060.719926] usb 2-1: new high speed USB device using ehci_hcd and address 7

```

and nothing else that seems to related to USB.

---

### Post by mnewell on 2007-11-29
Well, by process of elimination I'm pretty sure it's the hub.  I pulled everything off the hub and plugged the drives directly into the system and it ran a week with no problems.  I then put the original hub back in and three days later all the drives died.  Swapped in a different hub and all has been working flawlessly for over a week.

Of course the keyboard and mouse may also be a problem; I've not reconnected those yet.  But I'm betting at this point it's the original hub.  Odd since I put that hub in another (urk - Windoze) system and it's been working fine now for over a week...

Thanks!

Mike

---

