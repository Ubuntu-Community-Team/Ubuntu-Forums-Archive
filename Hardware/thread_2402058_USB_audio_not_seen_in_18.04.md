---
title: "USB audio not seen in 18.04"
date: 2018-09-25
forum: Hardware
---

### Post by SimonHGR on 2018-09-25
I've recently built a new system up with 18.04 and I'm finding that the USB audio interface that worked hours ago under 16.04 is not working.

If I plug it in, I get some pretty evil looking messages in dmesg:

```
[ 1221.554545] usb 3-12: new full-speed USB device number 9 using xhci_hcd
[ 1221.682492] usb 3-12: device descriptor read/64, error -71
[ 1221.918536] usb 3-12: device descriptor read/64, error -71
[ 1222.154454] usb 3-12: new full-speed USB device number 10 using xhci_hcd
[ 1222.282458] usb 3-12: device descriptor read/64, error -71
[ 1222.518436] usb 3-12: device descriptor read/64, error -71
[ 1222.626454] usb usb3-port12: attempt power cycle
[ 1223.278439] usb 3-12: new full-speed USB device number 11 using xhci_hcd
[ 1223.278753] usb 3-12: Device not responding to setup address.
[ 1223.486737] usb 3-12: Device not responding to setup address.
[ 1223.694352] usb 3-12: device not accepting address 11, error -71
[ 1223.822299] usb 3-12: new full-speed USB device number 12 using xhci_hcd
[ 1223.822514] usb 3-12: Device not responding to setup address.
[ 1224.030510] usb 3-12: Device not responding to setup address.
[ 1224.238350] usb 3-12: device not accepting address 12, error -71
[ 1224.238442] usb usb3-port12: unable to enumerate USB device
[ 1247.140651] usb 3-12: new full-speed USB device number 13 using xhci_hcd
[ 1247.268659] usb 3-12: device descriptor read/64, error -71
[ 1247.504730] usb 3-12: device descriptor read/64, error -71
[ 1247.740634] usb 3-12: new full-speed USB device number 14 using xhci_hcd
[ 1247.868720] usb 3-12: device descriptor read/64, error -71
[ 1248.104667] usb 3-12: device descriptor read/64, error -71
[ 1248.212711] usb usb3-port12: attempt power cycle
[ 1248.864598] usb 3-12: new full-speed USB device number 15 using xhci_hcd
[ 1248.864890] usb 3-12: Device not responding to setup address.
[ 1249.072872] usb 3-12: Device not responding to setup address.
[ 1249.280577] usb 3-12: device not accepting address 15, error -71
[ 1249.408569] usb 3-12: new full-speed USB device number 16 using xhci_hcd
[ 1249.408867] usb 3-12: Device not responding to setup address.
[ 1249.616855] usb 3-12: Device not responding to setup address.
[ 1249.824500] usb 3-12: device not accepting address 16, error -71
[ 1249.824577] usb usb3-port12: unable to enumerate USB device
[ 1276.206809] usb 3-10: new full-speed USB device number 17 using xhci_hcd
[ 1276.334843] usb 3-10: device descriptor read/64, error -71
[ 1281.750542] usb 3-10: device descriptor read/64, error -110
```

and the power light on the device (which is USB powered) remains off.

Where should I start looking to get this back to life?

---

### Post by SimonHGR on 2018-09-25
Well, I have solved this. It turns out that the long cable that I use on this (because the audio interface is connected to my mixing desk at the other end of my recording studio) was causing the problem. It was fine with the other hardware, but I guess the length of the cable caused a problem on the new USB hub, either because the new one is perhaps faster, or perhaps it has less drive capability to survive the 15 foot (or so) cable. Anyway, everything works with a short cable, so I guess I have to find a repeater, or something. Perhaps try to relocate some of the equipment.

---

