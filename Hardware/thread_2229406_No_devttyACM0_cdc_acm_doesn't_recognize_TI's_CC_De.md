---
title: "No /dev/ttyACM0: cdc_acm doesn't recognize TI's CC Debuggrer.  12.04"
date: 2014-06-12
forum: Hardware
---

### Post by mcclary on 2014-06-12
I have a laptop with a pretty stock Ubuntu 12.04 installed.

I'm trying to use the Texas Instruments CC Debugger and their CC2540 USB Evaluation Kit dongle.

The kernel recognized all the devices when they're plugged in.  But cdc_acm doesn't recognize them as ACM devices and doesn't create /dev/ttyACM0 for either of them.  (It recognizes a TRENDnet modem dongle just fine.)

(I've seen various advice about cdc_acm and everything says either
 - "it just works" with these TI devices or
 - you should use rmmod and modprobe-or-insmod to "bounce" cdc_acm to make sure you have the correct one and that it's freshly initialized {which I did but it didn't help})

dmesg outputs:

For plugging in the trendnet modem:

[ 9852.422832] usb 3-6: new full-speed USB device number 17 using xhci_hcd
[ 9854.870850] usb 3-6: New USB device found, idVendor=0572, idProduct=1329
[ 9854.870860] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9854.870866] usb 3-6: Product: USB Modem
[ 9854.870870] usb 3-6: Manufacturer: Conexant
[ 9854.870874] usb 3-6: SerialNumber: 24680246
[ 9854.871788] cdc_acm 3-6:1.0: ttyACM0: USB ACM device

For the CC Debugger:

[10458.295577] usb 3-6: new full-speed USB device number 22 using xhci_hcd
[10458.315337] usb 3-6: New USB device found, idVendor=0451, idProduct=16a2
[10458.315346] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10458.315351] usb 3-6: Product: CC Debugger
[10458.315356] usb 3-6: Manufacturer: Texas Instruments
[10458.315359] usb 3-6: SerialNumber: 00308126

For the CC2540 evaluation dongle:

[11951.231961] usb 3-6: new full-speed USB device number 23 using xhci_hcd
[11951.250081] usb 3-6: New USB device found, idVendor=0451, idProduct=16b3
[11951.250084] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[11951.250085] usb 3-6: Product: CC2540 USB Dongle
[11951.250086] usb 3-6: Manufacturer: Texas Instruments

---

