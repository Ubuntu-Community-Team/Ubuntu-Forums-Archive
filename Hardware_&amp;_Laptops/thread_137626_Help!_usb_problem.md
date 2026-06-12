---
title: "Help! usb problem"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by thetno on 2006-02-28
Initially after doing fresh install breezy, both scanner canon n650u and printer canon i550 works. but after sometime, before i knew it, printer just stopped working.

i updated the kernal to 2.6.14 and now scanner too stopped working.
but my usb mouse logitech m310 is still working fine, i can load usb thumbdrives.  

both scanner and printer works in windows xp.

checking out dmesg gives me this.  Tried googling for error -110, but haven't got much luck.

lsusb only show my mouse. and device manage doesn't list the printer and scanner


```
[4294672.551000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[4294672.917000] usb 2-3: new full speed USB device using ohci_hcd and address 2[4294673.037000] usb 2-3: device descriptor read/64, error -110
[4294673.258000] usb 2-3: device descriptor read/64, error -110
[4294673.472000] usb 2-3: new full speed USB device using ohci_hcd and address 3[4294673.592000] usb 2-3: device descriptor read/64, error -110
[4294673.813000] usb 2-3: device descriptor read/64, error -110
[4294674.027000] usb 2-3: new full speed USB device using ohci_hcd and address 4[4294674.431000] usb 2-3: device not accepting address 4, error -110
[4294674.544000] usb 2-3: new full speed USB device using ohci_hcd and address 5[4294674.948000] usb 2-3: device not accepting address 5, error -110
[4294674.948000] usbcore: registered new driver hiddev
[4294674.957000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2
[4294674.957000] usbcore: registered new driver usbhid
[4294674.957000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```

help.. T_T

thetno

---

### Post by lkz on 2006-03-01
I personally had some issues with usb hubs, even powered ones. My scanner wouldn't work through the hub, but fine directly connected to my computer.

---

### Post by thetno on 2006-03-01
Solved.
i don't know what happened, but when i unplugged my mouse, scanner can work, but not printer. if i unplug scanner, printer can work. i tried to unplug the internal usbcable and replugged and  everything works now.

---

