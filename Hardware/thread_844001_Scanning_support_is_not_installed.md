---
title: "Scanning support is not installed"
date: 2008-06-29
forum: Hardware
---

### Post by HyperHacker on 2008-06-29
I plugged in an Epson Perfection 610, and nothing seems to have happened. It lights up and moves around inside, but Kolourpaint says "Scanning support is not installed" and Gimp doesn't list any scanners. I don't know if this thing even works (was suspiciously cheap <_<), any way to tell?

---

### Post by PmDematagoda on 2008-06-29
Post the output of:-
```
dmesg | tail -25
```

---

### Post by HyperHacker on 2008-06-29
[quote=dmesg][188081.396225] eth0: no IPv6 routers present
[193259.867055] usb 2-1: new full speed USB device using uhci_hcd and address 2
[193260.053028] usb 2-1: configuration #1 chosen from 1 choice
[193260.519056] /build/buildd/linux-2.6.24/drivers/media/video/usbvideo/quickcam_messenger.c: Logitech Quickcam Messenger USB v0.01
[193260.566441] videodev: "QCM USB Camera" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[193260.566448] /build/buildd/linux-2.6.24/drivers/media/video/usbvideo/usbvideo.c: QCM on /dev/video1: canvas=320x240 videosize=320x240
[193260.566502] input: QCM button as /devices/pci0000:00/0000:00:10.1/usb2/2-1/input/input11
[193260.577093] usbcore: registered new interface driver QCM
[193260.760470] usbcore: registered new interface driver snd-usb-audio
[193690.916924] usb 5-4.1: new full speed USB device using ehci_hcd and address 22
[193692.257738] usb 5-4.1: configuration #1 chosen from 1 choice
[194059.169797] eth0: link down
[194116.565664] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[194116.566688] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[194132.552182] eth0: no IPv6 routers present
[195189.455635] usb 5-4.1: USB disconnect, address 22
[195193.491682] usb 5-4.1: new full speed USB device using ehci_hcd and address 23
[195194.752680] usb 5-4.1: configuration #1 chosen from 1 choice
[195744.192606] usb 5-4.1: USB disconnect, address 23
[196571.071400] atkbd.c: Unknown key pressed (translated set 2, code 0x95 on isa0060/serio0).
[196571.071407] atkbd.c: Use 'setkeycodes e015 <keycode>' to make it known.
[196571.109313] atkbd.c: Unknown key released (translated set 2, code 0x95 on isa0060/serio0).
[196571.109320] atkbd.c: Use 'setkeycodes e015 <keycode>' to make it known.
[198168.549149] usb 5-4.1: new full speed USB device using ehci_hcd and address 24
[198173.191722] usb 5-4.1: configuration #1 chosen from 1 choice[/quote](filler text to make this message at least one character)

---

### Post by PmDematagoda on 2008-06-29
After you remove the scanner and plug it back again, can you post the dmesg command again.

---

### Post by HyperHacker on 2008-06-29
Pretty much the same thing, just another few lines:
[quote=dmesg][198274.485580] usb 5-4.1: USB disconnect, address 24
[231412.597989] usb 5-4.1: new full speed USB device using ehci_hcd and address 25
[231417.057661] usb 5-4.1: configuration #1 chosen from 1 choice[/quote]

---

