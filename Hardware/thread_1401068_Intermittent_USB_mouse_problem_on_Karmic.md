---
title: "Intermittent USB mouse problem on Karmic"
date: 2010-02-07
forum: Hardware
---

### Post by insomniacity on 2010-02-07
Hi,

My karmic install on my Dell Vostro never used to have any trouble detecting my USB mouse. However, some change or upgrade in the last few months has created an issue whereby it refuses to recognise my mouse at first, and I have to repeatedly unplug it and plug it in again.

From /var/log/messages, many instances of unplug/plug in:

```
Feb  7 16:55:28 praxis kernel: [110814.992140] usb 6-2: new low speed USB device using uhci_hcd and address 8
Feb  7 16:55:28 praxis kernel: [110815.167152] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:28 praxis kernel: [110815.331933] usb 6-2: USB disconnect, address 8
Feb  7 16:55:31 praxis kernel: [110818.749079] usb 6-2: new low speed USB device using uhci_hcd and address 9
Feb  7 16:55:32 praxis kernel: [110818.923416] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:33 praxis kernel: [110819.960323] usb 6-2: USB disconnect, address 9
Feb  7 16:55:34 praxis kernel: [110821.440455] usb 6-2: new low speed USB device using uhci_hcd and address 10
Feb  7 16:55:34 praxis kernel: [110821.616045] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:35 praxis kernel: [110822.688134] usb 6-2: USB disconnect, address 10
Feb  7 16:55:37 praxis kernel: [110824.448080] usb 6-2: new low speed USB device using uhci_hcd and address 11
Feb  7 16:55:37 praxis kernel: [110824.622633] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:39 praxis kernel: [110825.912160] usb 6-2: USB disconnect, address 11
Feb  7 16:55:41 praxis kernel: [110827.996119] usb 6-2: new low speed USB device using uhci_hcd and address 12
Feb  7 16:55:41 praxis kernel: [110828.170914] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:42 praxis kernel: [110829.632082] usb 6-2: USB disconnect, address 12
Feb  7 16:55:44 praxis kernel: [110831.121133] usb 6-2: new low speed USB device using uhci_hcd and address 13
Feb  7 16:55:44 praxis kernel: [110831.295071] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:45 praxis kernel: [110832.360192] usb 6-2: USB disconnect, address 13
Feb  7 16:55:47 praxis kernel: [110834.744076] usb 6-2: new low speed USB device using uhci_hcd and address 14
Feb  7 16:55:48 praxis kernel: [110834.919300] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:48 praxis kernel: [110835.584156] usb 6-2: USB disconnect, address 14
Feb  7 16:55:50 praxis kernel: [110837.828080] usb 6-2: new low speed USB device using uhci_hcd and address 15
Feb  7 16:55:51 praxis kernel: [110838.003309] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:51 praxis kernel: [110838.808193] usb 6-2: USB disconnect, address 15
Feb  7 16:55:54 praxis kernel: [110840.932419] usb 6-2: new low speed USB device using uhci_hcd and address 16
Feb  7 16:55:54 praxis kernel: [110841.110317] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:55:56 praxis kernel: [110843.768176] usb 6-2: USB disconnect, address 16
Feb  7 16:55:59 praxis kernel: [110845.944084] usb 6-2: new low speed USB device using uhci_hcd and address 17
Feb  7 16:55:59 praxis kernel: [110846.119079] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:00 praxis kernel: [110847.240191] usb 6-2: USB disconnect, address 17
Feb  7 16:56:02 praxis kernel: [110849.560798] usb 6-2: new low speed USB device using uhci_hcd and address 18
Feb  7 16:56:02 praxis kernel: [110849.734289] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:04 praxis kernel: [110850.961290] usb 6-2: USB disconnect, address 18
Feb  7 16:56:08 praxis kernel: [110855.405721] usb 6-2: new low speed USB device using uhci_hcd and address 19
Feb  7 16:56:08 praxis kernel: [110855.583272] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:11 praxis kernel: [110858.648137] usb 6-2: USB disconnect, address 19
Feb  7 16:56:14 praxis kernel: [110861.076347] usb 6-2: new low speed USB device using uhci_hcd and address 20
Feb  7 16:56:14 praxis kernel: [110861.250346] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:16 praxis kernel: [110863.608166] usb 6-2: USB disconnect, address 20
Feb  7 16:56:19 praxis kernel: [110865.992321] usb 6-2: new low speed USB device using uhci_hcd and address 21
Feb  7 16:56:19 praxis kernel: [110866.166300] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:20 praxis kernel: [110867.576122] usb 6-2: USB disconnect, address 21
Feb  7 16:56:22 praxis kernel: [110869.776094] usb 6-2: new low speed USB device using uhci_hcd and address 22
Feb  7 16:56:23 praxis kernel: [110869.950350] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:25 praxis kernel: [110872.041163] usb 6-2: USB disconnect, address 22
Feb  7 16:56:27 praxis kernel: [110873.928069] usb 6-2: new low speed USB device using uhci_hcd and address 23
Feb  7 16:56:27 praxis kernel: [110874.103441] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:29 praxis kernel: [110876.256072] usb 6-2: USB disconnect, address 23
Feb  7 16:56:31 praxis kernel: [110878.276313] usb 6-2: new low speed USB device using uhci_hcd and address 24
Feb  7 16:56:31 praxis kernel: [110878.450139] usb 6-2: configuration #1 chosen from 1 choice
Feb  7 16:56:31 praxis kernel: [110878.817815] usbcore: registered new interface driver hiddev
Feb  7 16:56:31 praxis kernel: [110878.831264] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input12
Feb  7 16:56:31 praxis kernel: [110878.831345] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
Feb  7 16:56:31 praxis kernel: [110878.831361] usbcore: registered new interface driver usbhid
Feb  7 16:56:31 praxis kernel: [110878.831363] usbhid: v2.6:USB HID core driver

```

Why does it only recognise it on the 24th try?

My install is fully up to date.

---

### Post by AndrewAllen on 2010-02-08
I'm having the same problem with Karmic (9.04) on my Dell Inspiron 1501 and it's really frustrating. The usb mouse works occasionally and it's very erratic and unpredictable - it's a joy when it does work as I hate the built-in 'pad' mouse! I only wish there were some way I could control the functioning of the usb mouse and make it work - can somebody please tell me if there's a way I can do this?

---

### Post by chemamar on 2010-02-08
> **AndrewAllen said:**
> I'm having the same problem with Karmic (9.04) on my Dell Inspiron 1501 and it's really frustrating. The usb mouse works occasionally and it's very erratic and unpredictable - it's a joy when it does work as I hate the built-in 'pad' mouse! I only wish there were some way I could control the functioning of the usb mouse and make it work - can somebody please tell me if there's a way I can do this?

I have a netbook medion akoya and I have had to disable the touchpad in order to work with the usb mouse. In my case they are incompatible, either you work with one or with the other.

---

