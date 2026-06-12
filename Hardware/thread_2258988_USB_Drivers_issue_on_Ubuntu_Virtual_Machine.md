---
title: "USB Drivers issue on Ubuntu Virtual Machine"
date: 2015-01-01
forum: Hardware
---

### Post by blitzit on 2015-01-01
I am running Ubuntu 14.04 as a Virtual Machine (using VirtualBox) on Mac OS X Yosemite. I am using a MSP-FETU430IF (USB-Debug-Interface). The debugger is not being detected by the system. I am attaching the screenshot of the dmesg output after plugging the debugger into the USB port. I have the necessary drivers installed.
[IMG]http://e2e.ti.com/cfs-file/__key/communityserver-discussions-components-files/81/Ubuntu-Screenshot.png[/IMG]


Also, to cross-check the issue I tried plugging in the debugger in another Ubuntu desktop. This is not a VM. It has the same drivers installed - in fact lesser. The dmesg output is as follows:
[COLOR=#555555][FONT=Open Sans][ 1850.802398] usb 2-1.5: new full-speed USB device number 5 using ehci-pci[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.914951] usb 2-1.5: New USB device found, idVendor=0451, idProduct=f430[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.914956] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.914959] usb 2-1.5: Product: MSP-FET430UIF JTAG Tool[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.914961] usb 2-1.5: Manufacturer: Texas Instruments[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.914963] usb 2-1.5: SerialNumber: TUSB34101542110B7F5DFFD5[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1850.916623] ti_usb_3410_5052 2-1.5:1.0: TI USB 3410 1 port adapter converter detected[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.450690] usb 2-1.5: reset full-speed USB device number 5 using ehci-pci[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.547010] usb 2-1.5: device firmware changed[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.547127] ti_usb_3410_5052: probe of 2-1.5:1.0 failed with error -5[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.547354] usb 2-1.5: USB disconnect, device number 5[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.622755] usb 2-1.5: new full-speed USB device number 6 using ehci-pci[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.762737] usb 2-1.5: New USB device found, idVendor=0451, idProduct=f430[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.762742] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.762745] usb 2-1.5: Product: MSP-FET430UIF JTAG Tool[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.762747] usb 2-1.5: Manufacturer: Texas Instruments[/FONT][/COLOR]
[COLOR=#555555][FONT=Open Sans][ 1851.762749] usb 2-1.5: SerialNumber: TUSB34101542110B7F5DFFD5[/FONT][/COLOR]
[COLOR=#ff0000][FONT=Open Sans][ 1851.764153] ti_usb_3410_5052 2-1.5:1.0: TI USB 3410 1 port adapter converter detected[/FONT]
[FONT=Open Sans][ 1851.764173] ti_usb_3410_5052: probe of 2-1.5:1.0 failed with error -5[/FONT]
[FONT=Open Sans][ 1851.765531] ti_usb_3410_5052 2-1.5:2.0: TI USB 3410 1 port adapter converter detected[/FONT]
[FONT=Open Sans][ 1851.765675] usb 2-1.5: TI USB 3410 1 port adapter converter now attached to ttyUSB0[/FONT][/COLOR][COLOR=#555555][FONT=Open Sans]

Clearly, the connection initially fails here as well but a second attempt is made and the debugger is finally attached to ttyUSB0.

I have tried everything advised on similar problems reported earlier but nothing seems to work.[/FONT][/COLOR]

---

