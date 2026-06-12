---
title: "IR Remote doesn't work at all."
date: 2016-05-11
forum: Hardware
---

### Post by bdoe-att on 2016-05-11
I have a mceusb IR receiver that works on Windows, but not on my Ubuntu server/Kodi box.

I'm running Ubuntu 14.04, using kernel 3.13.0-85-generic, and Kodi 16.1

Neither irw nor ir-keytable return any values when I press any remote buttons. The little red light on my reciever lights up, so I know it's seeing the button presses.

From dmesg:
```
[11108.332521] usb 3-2: new full-speed USB device number 4 using xhci_hcd
[11108.350613] usb 3-2: New USB device found, idVendor=0471, idProduct=0815
[11108.350622] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11108.350626] usb 3-2: Product: eHome Infrared Transceiver
[11108.350630] usb 3-2: Manufacturer: Philips
[11108.350634] usb 3-2: SerialNumber: PH00Z6cz
[11108.351935] Registered IR keymap rc-rc6-mce
[11108.352165] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc1/input13
[11108.352304] rc1: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc1
[11108.352542] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input14
[11108.352907] rc rc1: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[11108.528840] mceusb 3-2:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[11108.528850] mceusb 3-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
```

From lsusb:
```
Bus 002 Device 002: ID 8087:8000 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

From ir-keytable:
```
Found /sys/class/rc/rc1/ (/dev/input/event2) with:
        Driver mceusb, table rc-rc6-mce
        Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Enabled protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other
        Name: Media Center Ed. eHome Infrared
        bus: 3, vendor/product: 0471:0815, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms
```

It appears that the receiver is being seen and recognized, but it's completely ignoring its input. By looking at my outputs above, is there anything I'm missing that would explain this? I would really like to get this to work, as presently I'm using a wireless keyboard to control Kodi, and that's rather awkward.

Let me know if you need output from anything else.

---

### Post by bdoe on 2016-05-14
Anybody have any idea of what's going on, or what's not working?

---

