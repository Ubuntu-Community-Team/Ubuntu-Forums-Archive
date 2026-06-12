---
title: "Microsoft USB mouse, Hotplug restart issue..."
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by sladed1 on 2005-04-28
Hi guys (& gals)

Im pretty new to linux, and I have just installed Ubuntu 5.04 I'm pretty impressed. I have this one small problem however, when I start the laptop (Toshiba Tecra 8000, P3 500, 196mb ram) the USB mouse (Microsoft Trackball Optical 1.0) doesnt apper to work, even though the led is active and is aware of movement. If i run the command [FONT=Courier New]sudo /etc/init.d/hotplug restart[/FONT] hot plug restarts as expected and I can then use the mouse. I have looked through the forum and I can't see anything that would help even though I found some problems that are simila. I've checked the BIOS, changed legacy support on and off, disabled & Renabled USB support and quite a few other 'low level' options.

Can anyone offer any pointers at this point? (no pun honest)  :-# 

Off topic... Gotta say, lovin linux, although it will never replace Microsoft Products in the general, i will definitly be ditchin Microsoft and migrating completly to linux :razz: 

Thanks Guys

Dan Slade
Lost in linux

---

### Post by ZiZe on 2005-04-28
try to look in
/var/log/user.log
/var/log/messages
/var/log/kern.log
in a terminal and se if you find anything like "usb.agent[18717]:  usbmouse: blacklisted"
i have the same issue, and have not been able to figure it out yet.

```

Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
Apr 28 17:27:24 jjameson kernel: PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.0: irq 16, io base 0xeec0
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 28 17:27:24 jjameson kernel: hub 1-0:1.0: USB hub found
Apr 28 17:27:24 jjameson kernel: hub 1-0:1.0: 2 ports detected
Apr 28 17:27:24 jjameson kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
Apr 28 17:27:24 jjameson kernel: PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.1: irq 19, io base 0xef00
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 28 17:27:24 jjameson kernel: hub 2-0:1.0: USB hub found
Apr 28 17:27:24 jjameson kernel: hub 2-0:1.0: 2 ports detected
Apr 28 17:27:24 jjameson kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
Apr 28 17:27:24 jjameson kernel: PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.2: irq 18, io base 0xef20
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 28 17:27:24 jjameson kernel: hub 3-0:1.0: USB hub found
Apr 28 17:27:24 jjameson kernel: hub 3-0:1.0: 2 ports detected
Apr 28 17:27:24 jjameson kernel: ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
Apr 28 17:27:24 jjameson kernel: usb 1-1: new low speed USB device using uhci_hcd and address 2
Apr 28 17:27:24 jjameson kernel: PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.3: irq 16, io base 0xef40
Apr 28 17:27:24 jjameson kernel: uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 28 17:27:24 jjameson kernel: hub 4-0:1.0: USB hub found
Apr 28 17:27:24 jjameson kernel: hub 4-0:1.0: 2 ports detected
Apr 28 17:27:25 jjameson kernel: input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1
Apr 28 17:27:25 jjameson kernel: input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1d.0-1

```

anyone that have any idea what it could be?

---

