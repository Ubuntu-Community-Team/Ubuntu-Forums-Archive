---
title: "USB Keyboard/mouse unplugged/plugged back in to work"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by Squawk on 2008-02-24
After booting my system I get to login but can´t type. Mouse works just fine, but the keyboard is completely unresponsive. If I unplug the keyboard and plug it back in still no joy. I have to unplug both the mouse and keyboard, and then plug in the keyboard, at which point the keyboard works. I can then plug in the mouse and everything is fine.  Both are usb devices, both work fine under gentoo linux and windows.  Output from dmesg shown below (you can tell what i was unplugging and plugging in given the sequences.

```
[   85.901948] usb 2-1: USB disconnect, address 6
[   87.700227] usb 2-1: new low speed USB device using ohci_hcd and address 7
[   87.803628] usb 2-1: configuration #1 chosen from 1 choice
[   87.810276] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input7
[   87.810302] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[   87.817575] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input8
[   87.817601] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[   89.479302] usb 2-1: USB disconnect, address 7
[   92.089591] usb 2-1: new low speed USB device using ohci_hcd and address 8
[   92.193028] usb 2-1: configuration #1 chosen from 1 choice
[   92.199670] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input9
[   92.199700] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[   92.206969] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input10
[   92.206999] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[   93.579810] usb 2-2: USB disconnect, address 3
[   97.387689] usb 2-1: USB disconnect, address 8
[  103.331578] usb 2-2: new low speed USB device using ohci_hcd and address 10
[  103.428578] usb 2-2: configuration #1 chosen from 1 choice
[  103.433023] input: Logitech USB-PS/2 Optical Mouse as /class/input/input11
[  103.433061] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2
[  105.337648] usb 2-1: new low speed USB device using ohci_hcd and address 11
[  108.864784] usb 2-1: new low speed USB device using ohci_hcd and address 12
[  112.313694] usb 2-1: new low speed USB device using ohci_hcd and address 13
[  112.416838] usb 2-1: configuration #1 chosen from 1 choice
[  112.423479] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input12
[  112.423508] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[  112.430786] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input13
[  112.430813] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1
[  113.613288] usb 2-1: USB disconnect, address 13
[  116.245869] usb 2-4: new low speed USB device using ohci_hcd and address 14
[  116.349045] usb 2-4: configuration #1 chosen from 1 choice
[  116.355680] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input14
[  116.355710] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-4
[  116.362988] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input15
[  116.363019] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-4
[  119.226626] usb 2-4: USB disconnect, address 14
[  119.671189] usb 2-2: USB disconnect, address 10
[  123.588709] usb 2-2: new low speed USB device using ohci_hcd and address 15
[  123.690052] usb 2-2: configuration #1 chosen from 1 choice
[  123.696684] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input16
[  123.696709] input: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-2
[  123.704004] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /class/input/input17
[  123.704031] input: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-2
[  127.547005] usb 2-1: new low speed USB device using ohci_hcd and address 16
[  127.641818] usb 2-1: configuration #1 chosen from 1 choice
[  127.646690] input: Logitech USB-PS/2 Optical Mouse as /class/input/input18
[  127.646730] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-1

```

I have an amd athlon 64 dual core proc, ubuntu was installed from livecd with no problems, livecd detects mouse and keyboard just fine. This happened from the first reboot into the new ubuntu install.

---

### Post by fewyun on 2008-02-24
I just had this same problem as well.

I have a microsoft ergonomics 2000 keyboard (new),  It was working, but after updates today, when I restarted the keyboard did not respond.

I found this:
[http://ubuntuforums.org/showthread.php?t=229559]("http://ubuntuforums.org/showthread.php?t=229559")

Which led me here: (to upgrade the kernel)
[http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755")

It worked great.

---

