---
title: "Wacom Bamboo autoconnect/hotplug"
date: 2009-11-10
forum: Hardware
---

### Post by scr4p3r on 2009-11-10
Hello,

I have a problem with autoconnecting/hotplug the Wacom (Bamboo, model MTE-450A). After a reboot the leds on the buttons are flashing and the tablet doesn't work, to get it to work I need to reconnect the USB cable to the tablet.

The system does recognize the Wacom, lsusb lists it but dmesg gives somewhat of a error during startup:
```

[    2.843053] usb 1-2.1: new full speed USB device using ehci_hcd and address 5
[    2.976055] usb 1-2.1: unable to read config index 0 descriptor/start: -32
[    2.976057] usb 1-2.1: chopping to 0 config(s)
[    2.982055] usb 1-2.1: string descriptor 0 read error: -32
[    2.982128] usb 1-2.1: no configuration chosen from 0 choices
```

After a reconnect dmesg shows:
```

[  476.967237] usb 1-2.1: USB disconnect, address 6
[  485.620165] usb 1-2.1: new full speed USB device using ehci_hcd and address 7
[  485.761180] usb 1-2.1: configuration #1 chosen from 1 choice
[  485.762001] input: Wacom Bamboo as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input7
```
 
I am running Ubuntu 9.10 x64 and no extra software installed for the Wacom.

Anyone ideas how to fix the this problem?

---

