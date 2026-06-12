---
title: "USB not detected."
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by chris_andrew on 2006-03-26
Hi,

I was given a USB stick/ fob the other day.  I was unable to retrieve the document from it.  When I plugged it in, I didn'tsee any indication of it being detected, ie: LED lighting-up on the stick.

Could anybody tell me where I am going wrong?

Thanks,

Chris.

---

### Post by Sutekh on 2006-03-27
Can you open a terminal window and enter this command```
tail -f /var/log/messages
```leave the window open and then plug in your USB.  Hopefully it will divulge some information on the device location (/dev/sd#) of the USB.

Then we can help you get access to the device.

---

### Post by chris_andrew on 2006-03-27
Hi,

The following is tail -f....USB inserted, USB removed.

Thanks,

Chris.

Mar 27 17:42:55 localhost usb.agent[20641]:      usb-storage: already loaded
Mar 27 17:42:57 localhost kernel: [4323284.401000] usb 4-3: USB disconnect, address 13
Mar 27 17:42:57 localhost kernel: [4323284.577000] usb 4-3: new high speed USB device using ehci_hcd and address 14
Mar 27 17:42:57 localhost kernel: [4323284.671000] scsi11 : SCSI emulation for USB Mass Storage devices
Mar 27 17:42:57 localhost usb.agent[20737]:      usb-storage: already loaded
Mar 27 17:42:58 localhost kernel: [4323284.901000] usb 4-3: USB disconnect, address 14
Mar 27 17:43:04 localhost kernel: [4323291.444000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Mar 27 17:43:04 localhost kernel: [4323291.444000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar 27 17:43:04 localhost kernel: [4323291.500000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Mar 27 17:43:04 localhost kernel: [4323291.500000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Mar 27 17:43:25 localhost kernel: [4323312.822000] usb 4-4: new high speed USB device using ehci_hcd and address 15
Mar 27 17:43:26 localhost kernel: [4323312.960000] usb 4-4: new high speed USB device using ehci_hcd and address 16
Mar 27 17:43:26 localhost kernel: [4323313.054000] scsi12 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:26 localhost usb.agent[20852]:      usb-storage: already loaded
Mar 27 17:43:26 localhost kernel: [4323313.401000] usb 4-4: USB disconnect, address 16
Mar 27 17:43:26 localhost kernel: [4323313.575000] usb 4-4: new high speed USB device using ehci_hcd and address 17
Mar 27 17:43:26 localhost kernel: [4323313.669000] scsi13 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:26 localhost usb.agent[20948]:      usb-storage: already loaded
Mar 27 17:43:27 localhost kernel: [4323313.901000] usb 4-4: USB disconnect, address 17
Mar 27 17:43:27 localhost kernel: [4323314.072000] usb 4-4: new high speed USB device using ehci_hcd and address 18
Mar 27 17:43:27 localhost kernel: [4323314.166000] scsi14 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:27 localhost usb.agent[21044]:      usb-storage: already loaded
Mar 27 17:43:27 localhost kernel: [4323314.401000] usb 4-4: USB disconnect, address 18
Mar 27 17:43:27 localhost kernel: [4323314.573000] usb 4-4: new high speed USB device using ehci_hcd and address 19
Mar 27 17:43:28 localhost kernel: [4323315.067000] usb 4-4: new high speed USB device using ehci_hcd and address 21
Mar 27 17:43:28 localhost kernel: [4323315.594000] usb 4-4: new high speed USB device using ehci_hcd and address 22
Mar 27 17:43:28 localhost kernel: [4323315.734000] scsi15 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:28 localhost usb.agent[21142]:      usb-storage: already loaded
Mar 27 17:43:29 localhost kernel: [4323315.901000] usb 4-4: USB disconnect, address 22
Mar 27 17:43:29 localhost kernel: [4323316.080000] usb 4-4: new high speed USB device using ehci_hcd and address 23
Mar 27 17:43:29 localhost kernel: [4323316.174000] scsi16 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:29 localhost usb.agent[21238]:      usb-storage: already loaded
Mar 27 17:43:29 localhost kernel: [4323316.401000] usb 4-4: USB disconnect, address 23
Mar 27 17:43:29 localhost kernel: [4323316.573000] usb 4-4: new high speed USB device using ehci_hcd and address 24
Mar 27 17:43:29 localhost kernel: [4323316.667000] scsi17 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:29 localhost usb.agent[21334]:      usb-storage: already loaded
Mar 27 17:43:30 localhost kernel: [4323317.401000] usb 4-4: USB disconnect, address 24
Mar 27 17:43:30 localhost kernel: [4323317.606000] usb 4-4: new high speed USB device using ehci_hcd and address 25
Mar 27 17:43:30 localhost kernel: [4323317.737000] scsi18 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:30 localhost usb.agent[21430]:      usb-storage: already loaded
Mar 27 17:43:31 localhost kernel: [4323317.901000] usb 4-4: USB disconnect, address 25
Mar 27 17:43:31 localhost kernel: [4323318.079000] usb 4-4: new high speed USB device using ehci_hcd and address 26
Mar 27 17:43:31 localhost kernel: [4323318.173000] scsi19 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:31 localhost usb.agent[21526]:      usb-storage: already loaded
Mar 27 17:43:31 localhost kernel: [4323318.401000] usb 4-4: USB disconnect, address 26
Mar 27 17:43:31 localhost kernel: [4323318.574000] usb 4-4: new high speed USB device using ehci_hcd and address 27
Mar 27 17:43:31 localhost kernel: [4323318.668000] scsi20 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:31 localhost usb.agent[21622]:      usb-storage: already loaded
Mar 27 17:43:32 localhost kernel: [4323318.901000] usb 4-4: USB disconnect, address 27
Mar 27 17:43:32 localhost kernel: [4323319.076000] usb 4-4: new high speed USB device using ehci_hcd and address 28
Mar 27 17:43:32 localhost kernel: [4323319.170000] scsi21 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:32 localhost usb.agent[21718]:      usb-storage: already loaded
Mar 27 17:43:33 localhost kernel: [4323320.151000] usb 4-4: USB disconnect, address 28
Mar 27 17:43:33 localhost kernel: [4323320.354000] usb 4-4: new high speed USB device using ehci_hcd and address 29
Mar 27 17:43:33 localhost kernel: [4323320.611000] scsi22 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:33 localhost usb.agent[21816]:      usb-storage: already loaded
Mar 27 17:43:34 localhost kernel: [4323321.401000] usb 4-4: USB disconnect, address 29
Mar 27 17:43:34 localhost kernel: [4323321.579000] usb 4-4: new high speed USB device using ehci_hcd and address 30
Mar 27 17:43:34 localhost kernel: [4323321.673000] scsi23 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:34 localhost usb.agent[21912]:      usb-storage: already loaded
Mar 27 17:43:35 localhost kernel: [4323321.901000] usb 4-4: USB disconnect, address 30
Mar 27 17:43:35 localhost kernel: [4323322.079000] usb 4-4: new high speed USB device using ehci_hcd and address 31
Mar 27 17:43:35 localhost kernel: [4323322.567000] usb 4-4: new high speed USB device using ehci_hcd and address 33
Mar 27 17:43:35 localhost kernel: [4323322.661000] scsi24 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:36 localhost usb.agent[22012]:      usb-storage: already loaded
Mar 27 17:43:36 localhost kernel: [4323323.652000] usb 4-4: USB disconnect, address 33
Mar 27 17:43:36 localhost kernel: [4323323.846000] usb 4-4: new high speed USB device using ehci_hcd and address 34
Mar 27 17:43:37 localhost kernel: [4323323.949000] scsi25 : SCSI emulation for USB Mass Storage devices
Mar 27 17:43:37 localhost kernel: [4323324.156000] usb 4-4: USB disconnect, address 34
Mar 27 17:43:37 localhost usb.agent[22109]:      usb-storage: already loaded
Mar 27 17:43:37 localhost kernel: [4323324.381000] usb 4-4: new high speed USB device using ehci_hcd and address 35

---

