---
title: "Problem with CH CS 568 USB joystick"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by ladoga on 2006-07-25
Hi.

Problem with this joystick is that it doesn't get properly initialized at boot. If i cat /dev/input/js0 and move the stick there's no input shown until i unplug the joystick and then replug it again after which it works fine until next reboot.

Here is output of "dmesg | grep usb" after boot:
```
[17179577.676000] usbcore: registered new driver usbfs
[17179577.676000] usbcore: registered new driver hub
[17179578.028000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179578.564000] usb 1-1: device not accepting address 2, error -71
[17179580.148000] usb 5-5: new high speed USB device using ehci_hcd and address 4
[17179580.828000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179581.268000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179581.708000] usb 3-2: new low speed USB device using uhci_hcd and address 2
[17179592.380000] usbcore: registered new driver hiddev
[17179592.408000] input: USB HID v1.00 Joystick [CH PRODUCTS CH COMBATSTICK USB] on usb-0000:00:10.0-1
[17179592.420000] input: USB HID v1.00 Joystick [CH PRODUCTS CH PRO PEDALS USB ] on usb-0000:00:10.1-2
[17179592.444000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-2
[17179592.444000] usbcore: registered new driver usbhid
[17179592.444000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
```

Here is output of dmesg after replugging the stick:
```
[17179665.736000] usb 1-1: USB disconnect, address 4
[17179667.640000] usb 1-1: new low speed USB device using uhci_hcd and address 5
[17179667.856000] input: CH PRODUCTS CH COMBATSTICK USB as /class/input/input6
[17179667.856000] input: USB HID v1.00 Joystick [CH PRODUCTS CH COMBATSTICK USB] on usb-0000:00:10.0-1
```

Any ideas what prevents joystick from initializing correctly when drivers get loaded at boot time? Maybe some issue with udev?

I've been in contact with other people sharing the exact same problem only common thing being the CH joystick or pedals, which rules out other hardware affecting this. So I presume it's somekind of bug.

Also if anyone can help me to figure out workaround for this - ie. how to simulate replug of joystick in software so i don't have to physically replug it after every reboot - it would be great.

I'm playing this nice flight sim [http://www.targetware.net/](http://www.targetware.net/) (it's in open beta and has native binaries for linux) so i really want to get my stick working without crawling on all fours under the desk.

[edit] Before hotplug was replaced by udev the joystick worked fine IIRC.

---

### Post by LWulf on 2006-07-31
I am having the same exact problem as Ladoga. I have also an Saitek X-36 HOTAS setup and M$ Wheel with pedals, both work ok, but to make the CH stick work I have to unplug and replug the CH joystick cable once I am in the OS.

 Cheers,
 Wulf

---

### Post by ladoga on 2006-09-04
Looks like it has been broken from 2.6.14 kernel onwards (or was that when udev came along?):
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg16285.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg16285.html)

As mentioned before inputs are registered correctly after replugging, so it's likely a timing issue. Problem affects whole CH Products USB device line, but it's already reported at linux-usb-users so maybe someone will do something about it.

---

### Post by Bazzaah on 2007-04-22
bump for this - having the exact same problem under Feisty....

does anyone know the answer to why this happens and what can be done about it?

---

