---
title: "DVB-T USB stick issues"
date: 2013-04-06
forum: Hardware
---

### Post by NicApicella on 2013-04-06
Hey guys!

I've been toying around with TV on Ubuntu, and it works out quite nice!

Based on my success and wonderful experience, I bought myself a new receiver with dual tuner: a "TerraTec Cinergy T USB Dual RC" to be specific.
After all, according to [http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_Dual_RC](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_T_USB_Dual_RC) , it should work just fine.

Unfortunately, I cannot seem to make it work. :-( And I'm pretty much a noob with regards to Linux' innards, so I'm asking you guys for help! :-)

When I plug it in, this happens ([FONT=courier new]dmesg [/FONT]output):

[FONT=courier new][86570.014724] usb 1-2: new high-speed USB device number 14 using ehci_hcd
[86570.151014] usb 1-2: New USB device found, idVendor=0ccd, idProduct=0099
[86570.151027] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[86570.151036] usb 1-2: Product: DVB-T TV Stick
[86570.151042] usb 1-2: Manufacturer: ITE Technologies, Inc.
[86572.152194] af9015: recv bulk message failed:-110
[86574.149760] af9015: recv bulk message failed:-110
[86576.147355] af9015: recv bulk message failed:-110
[86578.144761] af9015: recv bulk message failed:-110
[86578.144773] af9015: eeprom read failed=-1
[86578.144796] dvb_usb_af9015: probe of 1-2:1.0 failed with error -1
[86578.147570] input: ITE Technologies, Inc. DVB-T TV Stick as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.1/input/input17
[86578.147785] hid-generic 0003:0CCD:0099.000C: input,hidraw0: USB HID v1.01 Keyboard [ITE Technologies, Inc. DVB-T TV Stick] on usb-0000:00:12.2-2/input1[/FONT]

[FONT=courier new]lsusb [/FONT]says:[FONT=courier new]
Bus 001 Device 014: ID 0ccd:0099 TerraTec Electronic GmbH AfaTech 9015 [Cinergy T Stick Dual][/FONT]

As far as I can tell (googling around, comparing with my other DVB-T USB stick that works), after the "Manufacturer"-line, something different should happen: it should start loading the firmware, then register the newly found adapter. (Is that so? Again, I'm new at this; maybe I'm getting the steps wrong?)
Instead, I get those pesky "recv bulk message failed:-110", which I haven't managed to decode yet.

I have tried out everything that the linuxtv.org site suggested (downloading the new firmware, modifying the kernel module), to no avail.

Any hints or suggestions would be greatly appreciated! :-)

Regards,
Nicola

---

