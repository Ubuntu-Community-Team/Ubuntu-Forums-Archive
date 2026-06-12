---
title: "USB mouse slow, and clicking partially unresponsive after unplug/replug back in"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by pwozney on 2007-05-17
Hi,

Feisty is great; a perfect mix of slick preparation and the technical quirkiness that keeps me in touch with things.  :)  I have my keyboard and mouse connected to my system though a USB hub.

My mouse works great if I boot up with it, but if I remove it to use on another machine, and then bring it back, its action is seriously hampered.  On the second time plugging in the mouse, it tracks poorly, and only responds to half of the clicks I make.  In addition, sometimes keyboard response is slow.

This is pretty annoying, and although I can always reboot it really isn't a fix.  I suspect there is some process I can restart, but I'm not sure where to begin.  Any ideas?

Thanks,
Paul

---

### Post by pwozney on 2007-05-23
This is still a problem for me - my mouse will only respond to one out of every 5 clicks IF it is plugged in after Ubuntu is booted.

Does anyone have any ideas?

---

### Post by pwozney on 2007-05-29
This is the dmesg as I remove the usb stuff:
[INDENT][51900.376000] usb 5-1: USB disconnect, address 14
[51900.376000] usb 5-1.1: USB disconnect, address 16
[51900.376000] usb 5-1.3: USB disconnect, address 17
[51900.376000] usb 5-1.4: USB disconnect, address 18
[51900.376000] drivers/usb/class/usblp.c: usblp0: removed[/INDENT]

And as I plug it back in:
[INDENT][51911.024000] usb 5-1: new high speed USB device using ehci_hcd and address 19
[51911.156000] usb 5-1: configuration #1 chosen from 1 choice
[51911.156000] hub 5-1:1.0: USB hub found
[51911.156000] hub 5-1:1.0: 4 ports detected
[51911.464000] usb 5-1.1: new low speed USB device using ehci_hcd and address 20
[51911.564000] usb 5-1.1: configuration #1 chosen from 1 choice
[51911.572000] input: Logitech USB Receiver as /class/input/input20
[51911.572000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-1.1
[51911.772000] usb 5-1.3: new low speed USB device using ehci_hcd and address 21
[51911.872000] usb 5-1.3: configuration #1 chosen from 1 choice
[51911.876000] input: Darfon USB Combo Keyboard as /class/input/input21
[51911.876000] input: USB HID v1.00 Keyboard [Darfon USB Combo Keyboard] on usb-0000:00:1d.7-1.3
[51911.884000] input: Darfon USB Combo Keyboard as /class/input/input22
[51911.884000] input,hiddev96: USB HID v1.00 Device [Darfon USB Combo Keyboard] on usb-0000:00:1d.7-1.3
[51912.084000] usb 5-1.4: new high speed USB device using ehci_hcd and address 22
[51912.176000] usb 5-1.4: configuration #1 chosen from 1 choice
[51912.176000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 22 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1709[/INDENT]

This problem repeats itself very consistently.  Does anyone have any advice on where I can look?

Paul

---

### Post by pwozney on 2007-05-29
It is a little harder to pull out dmesg data for booting, but I found that usb/USB is only mentioned in a short span during bootup.  So here is the dmesg that is relevant to USB during boot - and this configuration is what actually works:

[INDENT][   50.066555] usbcore: registered new interface driver usbfs
[   50.066578] usbcore: registered new interface driver hub
[   50.066599] usbcore: registered new device driver usb
[   50.067368] USB Universal Host Controller Interface driver v3.0
[   50.067420] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 16
[   50.067430] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   50.067434] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   50.067573] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   50.067599] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eb00
[   50.067692] usb usb1: configuration #1 chosen from 1 choice
[   50.067714] hub 1-0:1.0: USB hub found
[   50.067719] hub 1-0:1.0: 2 ports detected
[   50.129187] ieee1394: Initialized config rom entry `ip1394'
[   50.171315] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   50.171328] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   50.171332] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   50.171355] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   50.171383] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ed00
[   50.171464] usb usb2: configuration #1 chosen from 1 choice
[   50.171488] hub 2-0:1.0: USB hub found
[   50.171492] hub 2-0:1.0: 2 ports detected
[   50.275227] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   50.275239] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   50.275243] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   50.275263] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   50.275291] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   50.275374] usb usb3: configuration #1 chosen from 1 choice
[   50.275396] hub 3-0:1.0: USB hub found
[   50.275401] hub 3-0:1.0: 2 ports detected
[   50.379105] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
[   50.379113] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   50.379117] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   50.379134] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   50.379159] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000e900
[   50.379232] usb usb4: configuration #1 chosen from 1 choice
[   50.379253] hub 4-0:1.0: USB hub found
[   50.379258] hub 4-0:1.0: 2 ports detected
[   50.484015] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 16
[   50.484030] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   50.484034] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   50.484059] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   50.484089] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   50.484096] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xd0240000
[   50.487990] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.488053] usb usb5: configuration #1 chosen from 1 choice
[   50.488079] hub 5-0:1.0: USB hub found
[   50.488085] hub 5-0:1.0: 8 ports detected
[   50.595132] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   50.646885] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[d0021000-d00217ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   50.654023] r8169 Gigabit Ethernet driver 2.2LK loaded
[   50.654039] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   50.654171] eth0: RTL8169s/8110s at 0xe0048000, 00:01:80:61:ea:be, IRQ 18
[   50.662411] SCSI subsystem initialized
[   50.667477] libata version 2.20 loaded.
[   50.672598] ata_piix 0000:00:1f.1: version 2.10ac1
[   50.672615] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   50.672632] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   50.672674] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   50.672700] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   50.672717] scsi0 : ata_piix[/INDENT]

So to re-iterate - on the initial boot with the USB stuff plugged in, everything is fine.  But if I remove the USB hub, and put it back in then my mouse works very badly.  Restarting X does not help.

---

### Post by pwozney on 2007-06-04
Any ideas?

Help!

---

### Post by pwozney on 2007-06-08
Bump.  Still a problem.

---

### Post by eentonig on 2007-06-08
I have the same issue.

I figure it's due to the improper removal of the device. I was actually searching for a command to 'unmount' the mice prior to removing it.

No luck so far.

---

### Post by pwozney on 2007-08-13
This is still a problem for me.

It is particularly annoying as it manifests itself when I come back from suspend, or hibernation.

---

### Post by pwozney on 2007-10-02
So anybody else have an idea?  I've pretty much given up on hibernation at this point as I can never get my mouse control back.

I would even be happy with some kind of a hack - if I could restart whatever needs to be restarted I would do it.

Anyone?  Anyone?

---

