---
title: "Canoscan not working- after Upgrade"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by mjmeche on 2007-04-23
lsusb
Bus 002 Device 006: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20

dmesg| grep usb
```

[   28.705291] usbcore: registered new interface driver usbfs
[   28.705316] usbcore: registered new interface driver hub
[   28.705338] usbcore: registered new device driver usb
[   28.706622] usb usb1: configuration #1 chosen from 1 choice
[   28.809172] usb usb2: configuration #1 chosen from 1 choice
[   28.913006] usb usb3: configuration #1 chosen from 1 choice
[   29.016805] usb usb4: configuration #1 chosen from 1 choice
[   29.126351] usb usb5: configuration #1 chosen from 1 choice
[   29.152362] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   29.951271] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   30.129126] usb 2-1: configuration #1 chosen from 1 choice
[   30.370702] usb 2-2: new full speed USB device using uhci_hcd and address 4
[   30.548478] usb 2-2: configuration #1 chosen from 1 choice
[   30.551567] usbcore: registered new interface driver hiddev
[   30.566595] input: USB HID v1.10 Keyboard [USB KVM Switch USB KVM Switch] on usb-0000:00:1d.1-1
[   30.579440] input: USB HID v1.10 Mouse [USB KVM Switch USB KVM Switch] on usb-0000:00:1d.1-1
[   30.579453] usbcore: registered new interface driver usbhid
[   30.579457] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  902.222135] usb 2-2: USB disconnect, address 4
[  909.020977] usb 2-2: new full speed USB device using uhci_hcd and address 5
[  909.193454] usb 2-2: configuration #1 chosen from 1 choice
[70163.597561] usb 2-2: USB disconnect, address 5
[70167.879797] usb 2-2: new full speed USB device using uhci_hcd and address 6
[70168.055128] usb 2-2: configuration #1 chosen from 1 choice

```

when tryng to scan through Xsane nothing but black scanner does not work, was working fine in Dapper

---

### Post by silentb on 2007-04-23
Same problem here. Scanner has worked in Edgy, but not in Feisty.

---

### Post by Argos_Bling on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This regression was introduced late in Feisty development, but the numerous bug postings (over 200 launchpad reports) don't seem to have resulted in any action. You may as well add your comments to the main bug thread, in the hope that something gets done.

Essentially the problem is that Ubuntu developers opted to activate an aggressive experimental kernel feature related to USB suspend, meaning that the scanner gets put to sleep during the initialisation stage of a scan.

---

### Post by mikeescott on 2007-09-26
> **silentb said:**
> Same problem here. Scanner has worked in Edgy, but not in Feisty.

I got it working!!!!!

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

---

