---
title: "ir-keytable not getting events from MCE remote"
date: 2013-11-15
forum: Hardware
---

### Post by P-J on 2013-11-15
Hi all,

Having problems getting a Microsoft RC6 MCE remote to work in Linux. I've had it working fine on a previous installation of Ubuntu 13.10, but for some reason it's not working now. Remote and receiver work fine on any Windows installation.

The main problem is that when I use : ```
sudo ir-keytables -p rc5,rc6 -t
```

I'm not seeing any codes generated from the remote. It's detected fine and dmesg says :

```

[ 1192.915597] usb 3-2: new full-speed USB device number 4 using xhci_hcd
[ 1192.933698] usb 3-2: New USB device found, idVendor=0609, idProduct=031d
[ 1192.933706] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1192.933710] usb 3-2: Product: eHome Infrared Transceiver
[ 1192.933713] usb 3-2: Manufacturer: SMK
[ 1192.933716] usb 3-2: SerialNumber: SM005h7v
[ 1192.934894] Registered IR keymap rc-rc6-mce
[ 1192.935020] input: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0/input16
[ 1192.935126] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0
[ 1192.935319] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input17
[ 1192.935506] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[ 1192.935512] xhci_queue_intr_tx: 2 callbacks suppressed
[ 1193.107767] mceusb 3-2:1.0: Registered SMK eHome Infrared Transceiver with mce emulator interface version 1
[ 1193.107770] mceusb 3-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)

```

When I had it working on a previous installation, I was able to do : ```
sudo cat /dev/input/eventX
``` ...and then I would see garbage when I pressed the remote keys. But since I've reinstalled I can't see that no matter which /dev/input/eventX device I query.

Does anyone have any suggestions of things I can try? The reason I'm so stumped is that before I reinstalled, it was plain sailing and this time it's a nightmare! There doesn't appear to be anything wrong except for the fact that I'm not getting the events! :)

Thanks :)

---

### Post by P-J on 2013-11-15
Nevermind.

After days of searching and endless testing, it turns out it was simply that it wouldn't work in a USB3.0 port. No idea why. As soon as I plugged it into a machine with USB2.0 ports, it worked straight way. Plugged it into the USB2.0 port on the troublesome machine and it worked again.

For anyone who is struggling with this issue, try a USB2.0 port if you have one (or buy a USB2.0 PCI card!)

---

