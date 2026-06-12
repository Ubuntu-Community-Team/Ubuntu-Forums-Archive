---
title: "USB woes with ASROCK K8NF6G-VSTA"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by leuzi on 2007-05-06
Hi!

I've been fighting USB troubles on a new machine built on a ASROCK K8NF6G-VSTA main board. More specifically, I can't use my USB mouse or keyboard.

The first odd thing is that I can't use the USB keyboard to enter the BIOS, as it's not recognized at that stage. Well I got a PS/2 keyboard and mouse and installed 7.04 anyway. But when booting into Ubuntu and plugging in the USB keyboard or mouse gives me errors like these:

```

[  950.754516] usb 1-7: new low speed USB device using ohci_hcd and address 22
[  950.938503] usb 1-7: device descriptor read/64, error -71
[  951.226507] usb 1-7: device descriptor read/64, error -71
[  951.506491] usb 1-7: new low speed USB device using ohci_hcd and address 23
[  951.690496] usb 1-7: device descriptor read/64, error -71
[  951.978480] usb 1-7: device descriptor read/64, error -71
[  965.094110] usb 1-8: new low speed USB device using ohci_hcd and address 25
[  965.278108] usb 1-8: device descriptor read/64, error -71
[  965.566098] usb 1-8: device descriptor read/64, error -71
[  965.846089] usb 1-8: new low speed USB device using ohci_hcd and address 26
[  966.030087] usb 1-8: device descriptor read/64, error -71
[  966.318077] usb 1-8: device descriptor read/64, error -71
[  966.598069] usb 1-8: new low speed USB device using ohci_hcd and address 27
[  967.014056] usb 1-8: device not accepting address 27, error -71
[  967.190046] usb 1-8: new low speed USB device using ohci_hcd and address 28
[  967.606042] usb 1-8: device not accepting address 28, error -71
```

Interesting detail: I tried an older USB mouse device, and surprisingly that one works flawlessly.

Things I already tried:

[LIST]
[*] I flashed the BIOS to the most recent version (1.60)
[*] I blacklisted the ehci_hcd module as suggested in several forum threads and/or bug reports I found
[*] I tried booting with the "irqpoll" and "acpi=off" options
[*] I both disabled and enabled the "Legacy USB Support" option in the BIOS
[*] I both disabled and enabled the USB 2.0 compatibility in the BIOS
[/LIST]

I also tried a third-party PCI USB hub, but that device didn't work at all. Instead I keep getting "hub xy: over-current change on port z" error messages, even if there aren't any devices connected to the hub.

I'm really at a loss here and I'd really appreciate some good advice!

Thanks in advance,
Christoph

---

### Post by leuzi on 2007-05-16
I finally gave up on the ASROCK board and replaced it by an ASUS K8V-VM. This board shows no USB problems; in fact both the on board USB ports **and** the additional PCI USB hub (that wouldn't work with the ASROCK board) work flawlessly.

Cheers,
  Christoph

---

