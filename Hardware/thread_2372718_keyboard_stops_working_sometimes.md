---
title: "keyboard stops working sometimes"
date: 2017-09-28
forum: Hardware
---

### Post by mdnak on 2017-09-28
keyboard stops working intermittently..It works when I 
- unplug both the mouse and keyboard, wait for some time, plug in keyboard first and then the mouse.
It wont work if i just plug out the keyboard and plug it back in.
Here are the dmesg errors:
```
[[   38.056436] usb 1-8: new full-speed USB device number 18 using xhci_hcd
[   38.168435] usb 1-8: device descriptor read/64, error -71
[   39.296329] usb 1-8: new full-speed USB device number 21 using xhci_hcd
[   40.288238] usb 1-8: new full-speed USB device number 24 using xhci_hcd
[   40.400273] usb 1-8: device descriptor read/64, error -71
[   40.616187] usb 1-8: device descriptor read/64, error -71
[   40.832145] usb 1-8: new full-speed USB device number 25 using xhci_hcd
[   40.944201] usb 1-8: device descriptor read/64, error -71
[   41.160220] usb 1-8: device descriptor read/64, error -71
[   41.792125] usb 1-8: new full-speed USB device number 27 using xhci_hcd
[   41.904108] usb 1-8: device descriptor read/64, error -71
[   42.120077] usb 1-8: device descriptor read/64, error -71
[   42.820065] usb 1-8: new full-speed USB device number 30 using xhci_hcd
[   42.931970] usb 1-8: device descriptor read/64, error -71
[   47.391656] usb 1-8: new full-speed USB device number 47 using xhci_hcd
[   47.503568] usb 1-8: device descriptor read/64, error -71
[   47.719625] usb 1-8: device descriptor read/64, error -71
[   48.179591] usb 1-8: new full-speed USB device number 49 using xhci_hcd
[   48.529445] usb 1-8: new full-speed USB device number 50 using xhci_hcd
[   48.641801] usb 1-8: device descriptor read/64, error -71
[   48.909467] usb 1-8: device descriptor read/64, error -71
[   49.173144] usb 1-8: new full-speed USB device number 51 using xhci_hcd
[   49.336834] usb 1-8: device descriptor read/64, error -71
[   49.601689] usb 1-8: device descriptor read/64, error -71
[   49.870236] usb 1-8: new full-speed USB device number 52 using xhci_hcd
[   49.870430] usb 1-8: Device not responding to setup address.
[   50.068991] usb 1-8: Device not responding to setup address.
[   50.267764] usb 1-8: device not accepting address 52, error -71
[   50.670199] usb 1-8: new full-speed USB device number 54 using xhci_hcd
[   50.834260] usb 1-8: device descriptor read/64, error -71
[   51.099869] usb 1-8: device descriptor read/64, error -71
[   51.366088] usb 1-8: new full-speed USB device number 55 using xhci_hcd
[   52.098994] usb 1-8: new full-speed USB device number 57 using xhci_hcd
[   53.073003] usb 1-8: new full-speed USB device number 60 using xhci_hcd
[   54.285822] usb 1-8: new full-speed USB device number 64 using xhci_hcd
[   54.451474] usb 1-8: device descriptor read/64, error -71
[   56.252501] usb 1-8: new full-speed USB device number 70 using xhci_hcd
[   56.363330] usb 1-8: device descriptor read/64, error -71
[   56.818521] usb 1-8: new full-speed USB device number 71 using xhci_hcd
[   56.988714] usb 1-8: device descriptor read/64, error -71
[   58.205328] usb 1-8: new full-speed USB device number 75 using xhci_hcd
[   63.886693] usb 1-8: new full-speed USB device number 97 using xhci_hcd
[   63.998247] usb 1-8: device descriptor read/64, error -71
[   64.631851] usb 1-8: new full-speed USB device number 98 using xhci_hcd
[   72.785188] usb 1-8: new full-speed USB device number 6 using xhci_hcd
[   72.897067] usb 1-8: device descriptor read/64, error -71
[   73.112902] usb 1-8: device descriptor read/64, error -71
[   73.328620] usb 1-8: new full-speed USB device number 7 using xhci_hcd
[   73.440528] usb 1-8: device descriptor read/64, error -71
[   73.656210] usb 1-8: device descriptor read/64, error -71
[   73.871961] usb 1-8: new full-speed USB device number 8 using xhci_hcd
[   73.872181] usb 1-8: Device not responding to setup address.
[   74.075735] usb 1-8: Device not responding to setup address.
[   74.279514] usb 1-8: device not accepting address 8, error -71
[   74.631145] usb 1-8: new full-speed USB device number 10 using xhci_hcd
[   74.743192] usb 1-8: device descriptor read/64, error -71
[   74.958854] usb 1-8: device descriptor read/64, error -71
[   75.174595] usb 1-8: new full-speed USB device number 11 using xhci_hcd
[   75.286554] usb 1-8: device descriptor read/64, error -71
[   75.981881] usb 1-8: new full-speed USB device number 13 using xhci_hcd
[   76.093803] usb 1-8: device descriptor read/64, error -71
[   76.309633] usb 1-8: device descriptor read/64, error -71
[   77.004998] usb 1-8: new full-speed USB device number 16 using xhci_hcd
[   77.116973] usb 1-8: device descriptor read/64, error -71
[   77.332815] usb 1-8: device descriptor read/64, error -71
[   77.548592] usb 1-8: new full-speed USB device number 17 using xhci_hcd
[   77.660571] usb 1-8: device descriptor read/64, error -71
[   77.876440] usb 1-8: device descriptor read/64, error -71
[   78.092119] usb 1-8: new full-speed USB device number 18 using xhci_hcd
[   78.092218] usb 1-8: Device not responding to setup address.
[   78.296286] usb 1-8: Device not responding to setup address.
[   78.499871] usb 1-8: device not accepting address 18, error -71
[   78.851715] usb 1-8: new full-speed USB device number 20 using xhci_hcd
[   78.963683] usb 1-8: device descriptor read/64, error -71
[   79.179586] usb 1-8: device descriptor read/64, error -71
[   79.395383] usb 1-8: new full-speed USB device number 21 using xhci_hcd
[   79.507363] usb 1-8: device descriptor read/64, error -71
[   79.723088] usb 1-8: device descriptor read/64, error -71
[   79.939059] usb 1-8: new full-speed USB device number 22 using xhci_hcd
[   79.939276] usb 1-8: Device not responding to setup address.
[   80.143168] usb 1-8: Device not responding to setup address.
[   80.346828] usb 1-8: device not accepting address 22, error -71
[   80.698541] usb 1-8: new full-speed USB device number 24 using xhci_hcd
[   80.810478] usb 1-8: device descriptor read/64, error -71
[   81.026181] usb 1-8: device descriptor read/64, error -71
[   81.241474] usb 1-8: new full-speed USB device number 25 using xhci_hcd
[   81.353194] usb 1-8: device descriptor read/64, error -71
[   81.568700] usb 1-8: device descriptor read/64, error -71
[   81.784018] usb 1-8: new full-speed USB device number 26 using xhci_hcd
[   81.784236] usb 1-8: Device not responding to setup address.
[   81.987850] usb 1-8: Device not responding to setup address.
[   82.190841] usb 1-8: device not accepting address 26, error -71
[   82.541773] usb 1-8: new full-speed USB device number 28 using xhci_hcd
[   82.653638] usb 1-8: device descriptor read/64, error -71
[   82.869037] usb 1-8: device descriptor read/64, error -71
[   83.084302] usb 1-8: new full-speed USB device number 29 using xhci_hcd
[   83.196165] usb 1-8: device descriptor read/64, error -71
[   83.411606] usb 1-8: device descriptor read/64, error -71
[   83.626939] usb 1-8: new full-speed USB device number 30 using xhci_hcd
[   83.627159] usb 1-8: Device not responding to setup address.
[   83.830553] usb 1-8: Device not responding to setup address.
[   84.033854] usb 1-8: device not accepting address 30, error -71
[   84.385047] usb 1-8: new full-speed USB device number 32 using xhci_hcd
[   84.496775] usb 1-8: device descriptor read/64, error -71
[   84.712236] usb 1-8: device descriptor read/64, error -71
[   84.927546] usb 1-8: new full-speed USB device number 33 using xhci_hcd
[   85.039432] usb 1-8: device descriptor read/64, error -71
[   85.254838] usb 1-8: device descriptor read/64, error -71
[   85.470290] usb 1-8: new full-speed USB device number 34 using xhci_hcd
[   85.470466] usb 1-8: Device not responding to setup address.
[   85.674141] usb 1-8: Device not responding to setup address.
[   85.877421] usb 1-8: device not accepting address 34, error -71
[   86.412066] usb 1-8: new full-speed USB device number 36 using xhci_hcd
[   86.523899] usb 1-8: device descriptor read/64, error -71
[   86.739455] usb 1-8: device descriptor read/64, error -71
[   97.748870] usb 1-8: new low-speed USB device number 80 using xhci_hcd
[   97.885822] usb 1-8: New USB device found, idVendor=0e8f, idProduct=0021
[   97.885824] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   97.885825] usb 1-8: Product: USB Keyboard
[   97.885826] usb 1-8: Manufacturer: CZW
[   97.885939] usb 1-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   97.885942] usb 1-8: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[   97.888861] input: CZW USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/0003:0E8F:0021.0009/input/input23
[   97.944809] hid-generic 0003:0E8F:0021.0009: input,hidraw1: USB HID v1.10 Keyboard [CZW USB Keyboard] on usb-0000:00:14.0-8/input0
[   97.945404] usbhid 1-8:1.1: can't add hid device: -71
/CODE][  242.691911] usb 1-8: new low-speed USB device number 14 using xhci_hcd
[  242.824434] usb 1-8: New USB device found, idVendor=1c4f, idProduct=0034
[  242.824442] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  242.824447] usb 1-8: Product: Usb Mouse
[  242.824450] usb 1-8: Manufacturer: SIGMACHIP
[  242.824755] usb 1-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  242.827597] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/0003:1C4F:0034.0028/input/input54
[  242.828050] hid-generic 0003:1C4F:0034.0028: input,hidraw2: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-8/input0
[  244.127233] usb 1-7: reset low-speed USB device number 13 using xhci_hcd
[  244.386911] usb 1-7: Device not responding to setup address.
[  244.590732] usb 1-7: Device not responding to setup address.
[  244.794586] usb 1-7: device not accepting address 13, error -71
[  244.998592] usb 1-7: USB disconnect, device number 13
[  245.330262] usb 1-7: new low-speed USB device number 15 using xhci_hcd
[  245.463535] usb 1-7: New USB device found, idVendor=0e8f, idProduct=0021
[  245.463543] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  245.463547] usb 1-7: Product: USB Keyboard
[  245.463551] usb 1-7: Manufacturer: CZW
[  245.463853] usb 1-7: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  245.463867] usb 1-7: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[  245.467497] input: CZW USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:0E8F:0021.0029/input/input55
[  245.522769] hid-generic 0003:0E8F:0021.0029: input,hidraw0: USB HID v1.10 Keyboard [CZW USB Keyboard] on usb-0000:00:14.0-7/input0
[  245.526644] input: CZW USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:0E8F:0021.002A/input/input56
[  245.582529] hid-generic 0003:0E8F:0021.002A: input,hidraw1: USB HID v1.10 Device [CZW USB Keyboard] on usb-0000:00:14.0-7/input1
```

---

### Post by Autodave on 2017-09-28
First, have you tried another keyboard and mouse? That would be my first step.

Second, how many unpowered USB devices are hooked up?  Have you tried removing them and seeing what happens? It could be that you have too many items using the power available or you could have a weak/failing power supply.

---

