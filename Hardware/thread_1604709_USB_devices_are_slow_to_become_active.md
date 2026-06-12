---
title: "USB devices are slow to become active"
date: 2010-10-24
forum: Hardware
---

### Post by supernicko on 2010-10-24
Hi folks,

Recently installed 10.10, but had the same issue when I last tried out 10.4.

During the install process and initial boot into the system, I've had no issues with my usb keyboard or mouse.

After I have installed the nvidia restricted drivers and enabled twinview, it can take up to 5 minutes for my usb keyboard and mouse to be detected and become responsive.

This also happens when I boot into recovery mode.

This is quite annoying as due to work I will need to dual boot into a Windows partition on a daily basis.

Relevant parts from /var/log/messages are quoted below

```

Oct 25 01:02:50 Farnsworth kernel: [   31.730014] usb 1-3: new high speed USB device using ehci_hcd and address 3
Oct 25 01:03:10 Farnsworth kernel: [   52.230017] usb 1-3: new high speed USB device using ehci_hcd and address 4
Oct 25 01:03:21 Farnsworth kernel: [   62.620013] usb 1-3: new high speed USB device using ehci_hcd and address 5
Oct 25 01:03:31 Farnsworth kernel: [   73.050019] usb 1-4: new high speed USB device using ehci_hcd and address 6
Oct 25 01:03:31 Farnsworth kernel: [   73.200568] usb 1-4: config 1 has an invalid interface number: 3 but max is 2
Oct 25 01:03:31 Farnsworth kernel: [   73.200571] usb 1-4: config 1 has no interface number 2
Oct 25 01:03:31 Farnsworth kernel: [   73.249944] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 25 01:03:31 Farnsworth kernel: [   73.253746] usbcore: registered new interface driver snd-usb-audio
Oct 25 01:03:31 Farnsworth kernel: [   73.274804] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 25 01:03:31 Farnsworth kernel: [   73.276306] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 25 01:03:32 Farnsworth kernel: [   73.720013] usb 4-1: new full speed USB device using uhci_hcd and address 2
Oct 25 01:04:02 Farnsworth kernel: [  104.300013] usb 4-1: new full speed USB device using uhci_hcd and address 3
Oct 25 01:04:33 Farnsworth kernel: [  134.880013] usb 4-1: new full speed USB device using uhci_hcd and address 4
Oct 25 01:04:43 Farnsworth kernel: [  145.260012] usb 4-1: new full speed USB device using uhci_hcd and address 5
Oct 25 01:04:54 Farnsworth kernel: [  155.800014] usb 5-1: new low speed USB device using uhci_hcd and address 2
Oct 25 01:04:54 Farnsworth kernel: [  155.992190] usbcore: registered new interface driver hiddev
Oct 25 01:04:54 Farnsworth kernel: [  156.006765] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2
Oct 25 01:04:54 Farnsworth kernel: [  156.006871] generic-usb 0003:046D:C408.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1a.2-1/input0
Oct 25 01:04:54 Farnsworth kernel: [  156.006892] usbcore: registered new interface driver usbhid
Oct 25 01:04:54 Farnsworth kernel: [  156.006894] usbhid: USB HID core driver
Oct 25 01:04:54 Farnsworth kernel: [  156.260013] usb 5-2: new low speed USB device using uhci_hcd and address 3
Oct 25 01:04:55 Farnsworth kernel: [  156.466556] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3
Oct 25 01:04:55 Farnsworth kernel: [  156.466660] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1a.2-2/input0
Oct 25 01:04:55 Farnsworth kernel: [  156.490399] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.1/input/input4
Oct 25 01:04:55 Farnsworth kernel: [  156.490496] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1a.2-2/input1
Oct 25 01:04:55 Farnsworth kernel: [  156.720015] usb 6-1: new full speed USB device using uhci_hcd and address 2
Oct 25 01:04:55 Farnsworth kernel: [  156.909763] input: Asus gaming Mouse (G112) as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5
Oct 25 01:04:55 Farnsworth kernel: [  156.909873] generic-usb 0003:0461:4D99.0004: input,hidraw3: USB HID v1.11 Mouse [Asus gaming Mouse (G112)] on usb-0000:00:1d.0-1/input0
Oct 25 01:05:29 Farnsworth kernel: [  190.719903] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 25 01:05:29 Farnsworth kernel: [  190.720770] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 25 01:05:29 Farnsworth kernel: [  190.724653] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.


```

---

### Post by supernicko on 2010-10-24
Some further investigation reveals that this could be related to udev. Would it be better to set these devices up in some sort of udev config so it isn't hanging to find the keyboard and mouse at least? 

I'm pretty new to dealing with udev configs so any info would be appreciated.

---

