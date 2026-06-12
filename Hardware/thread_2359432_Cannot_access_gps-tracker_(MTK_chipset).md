---
title: "Cannot access gps-tracker (MTK chipset)"
date: 2017-04-24
forum: Hardware
---

### Post by watercress on 2017-04-24
Dear community,

I fail to access tracking data collected with [COLOR=#000000][FONT=&amp]Transystem iBlue 747. The device is switched on and is probably recognized (ubuntu 16.04). [/FONT][/COLOR]It is also reported that it works well under ubuntu.[COLOR=#000000][FONT=&amp]

dmesg returns
[/FONT][/COLOR]```
[10732.486187] usb 1-3: new full-speed USB device number 9 using xhci_hcd
[10732.615868] usb 1-3: New USB device found, idVendor=0e8d, idProduct=3329
[10732.615876] usb 1-3: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[10732.615881] usb 1-3: Product: GPS Receiver
[10732.615884] usb 1-3: Manufacturer: MTK
[10732.652615] cdc_acm 1-3:1.1: ttyACM0: USB ACM device
[10732.652960] usbcore: registered new interface driver cdc_acm
[10732.652965] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[10742.580744] usb 1-3: USB disconnect, device number 9
[10946.412494] usb 1-3: new full-speed USB device number 10 using xhci_hcd
[10946.542155] usb 1-3: New USB device found, idVendor=0e8d, idProduct=3329
[10946.542163] usb 1-3: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[10946.542168] usb 1-3: Product: GPS Receiver
[10946.542172] usb 1-3: Manufacturer: MTK
[10946.543761] cdc_acm 1-3:1.1: ttyACM0: USB ACM device
[11077.904248] usb 1-3: USB disconnect, device number 10
[11082.276458] usb 1-4: new full-speed USB device number 11 using xhci_hcd
[11082.407552] usb 1-4: New USB device found, idVendor=0e8d, idProduct=3329
[11082.407556] usb 1-4: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[11082.407558] usb 1-4: Product: GPS Receiver
[11082.407560] usb 1-4: Manufacturer: MTK
[11082.409318] cdc_acm 1-4:1.1: ttyACM0: USB ACM device
[12657.261587] usb 1-4: USB disconnect, device number 11
[12683.186634] usb 3-2: new full-speed USB device number 2 using xhci_hcd
[12683.547250] usb 3-2: New USB device found, idVendor=0e8d, idProduct=3329
[12683.547258] usb 3-2: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[12683.547263] usb 3-2: Product: GPS Receiver
[12683.547267] usb 3-2: Manufacturer: MTK
[12683.556092] cdc_acm 3-2:1.1: ttyACM0: USB ACM device
[12944.787597] usb 3-2: USB disconnect, device number 2
[12951.538455] usb 1-12: new full-speed USB device number 13 using xhci_hcd
[12951.668689] usb 1-12: New USB device found, idVendor=0e8d, idProduct=3329
[12951.668697] usb 1-12: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[12951.668702] usb 1-12: Product: GPS Receiver
[12951.668706] usb 1-12: Manufacturer: MTK
[12951.670426] cdc_acm 1-12:1.1: ttyACM0: USB ACM device
[13105.764639] usb 1-12: USB disconnect, device number 13
[13106.130976] usb 1-12: new full-speed USB device number 14 using xhci_hcd
[13106.260734] usb 1-12: New USB device found, idVendor=0e8d, idProduct=3329
[13106.260741] usb 1-12: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[13106.260746] usb 1-12: Product: GPS Receiver
[13106.260750] usb 1-12: Manufacturer: MTK
[13106.262350] cdc_acm 1-12:1.1: ttyACM0: USB ACM device
[13386.467428] usb 1-12: USB disconnect, device number 14
[13386.839120] usb 1-12: new full-speed USB device number 15 using xhci_hcd
[13386.968834] usb 1-12: New USB device found, idVendor=0e8d, idProduct=3329
[13386.968841] usb 1-12: New USB device strings: Mfr=3, Product=4, SerialNumber=0
[13386.968846] usb 1-12: Product: GPS Receiver
[13386.968850] usb 1-12: Manufacturer: MTK
[13386.970456] cdc_acm 1-12:1.1: ttyACM0: USB ACM device
```[COLOR=#000000][FONT=&amp]


[/FONT][/COLOR][COLOR=#000000][FONT=&amp]lsusb returns
[/FONT][/COLOR]```
Bus 001 Device 015: ID 0e8d:3329 MediaTek Inc. Qstarz BT-Q1000XT
```[COLOR=#000000][FONT=&amp]

I tried to download the tracks using mtkbabel but am aked if the device is switched on.

[/FONT][/COLOR]```
mtkbabel  /dev/ttyACM0 -f test -c
Cannot open /dev/ttyUSB0. Did you switch ON the GPS device?
```[COLOR=#000000][FONT=&amp]

No success with bt747 and gpsd, too.

Any hints are highly appreciated. Sorry for my limited skills. I would be very happy if we can avoid using Windows since I recently pushed through the installation of linux on my working station at the University [/FONT][/COLOR];)[COLOR=#000000][FONT=&amp]
Cheers,
jens[/FONT][/COLOR]

---

### Post by watercress on 2017-04-27
Solved. Thanks to user march!! 
> The issue with the permissions for /dev/ttyACM0 can be permanantly solved by adding yourself to the dialout group. You will have to logout and then log back in before the group change is recognized.


You can do this with sudo usermod -a -G dialout terrik if terrik is your username.


---

