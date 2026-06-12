---
title: "USB mouse keeps disconnecting"
date: 2019-11-17
forum: Hardware
---

### Post by wonger33 on 2019-11-17
My USB mouse keeps disconnecting every few minutes, sometimes multiple times a minute.  I tried another mouse and it does the same thing. This constant disconnection and reconnection causes the mouse to stutter and lag. I'm using kubuntu 18.04.3 and I have installed all software updates.  My system's CPU is a Pentium G4400. I've tried different USB ports and it still does this.  Does anyone know how to fix this?  This is what the system log shows:

```
[  850.896437] usb 1-6: USB disconnect, device number 5
[  851.284189] usb 1-6: new low-speed USB device number 6 using xhci_hcd
[  851.620015] usb 1-6: device descriptor read/64, error -71
[  851.881127] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[  851.881132] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[  851.881136] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[  851.881138] usb 1-6: Manufacturer: Microsoft
[  851.888706] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.0005/input/input21
[  851.948520] hid-generic 0003:045E:0040.0005: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0
[  924.227487] usb 1-6: USB disconnect, device number 6
[  924.613563] usb 1-6: new low-speed USB device number 7 using xhci_hcd
[  924.766852] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[  924.766858] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[  924.766861] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[  924.766864] usb 1-6: Manufacturer: Microsoft
[  924.770631] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.0006/input/input22
[  924.772099] hid-generic 0003:045E:0040.0006: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0
[  952.322836] usb 1-6: USB disconnect, device number 7
[  952.696101] usb 1-6: new low-speed USB device number 8 using xhci_hcd
[  952.849019] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[  952.849024] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[  952.849027] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[  952.849030] usb 1-6: Manufacturer: Microsoft
[  952.852364] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.0007/input/input23
[  952.852828] hid-generic 0003:045E:0040.0007: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0
[ 1167.088385] usb 1-6: USB disconnect, device number 8
[ 1167.472810] usb 1-6: new low-speed USB device number 9 using xhci_hcd
[ 1167.625920] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[ 1167.625925] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 1167.625929] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[ 1167.625932] usb 1-6: Manufacturer: Microsoft
[ 1167.629660] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.0008/input/input24
[ 1167.689389] hid-generic 0003:045E:0040.0008: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0
[ 1181.534359] usb 1-6: USB disconnect, device number 9
[ 1181.924206] usb 1-6: new low-speed USB device number 10 using xhci_hcd
[ 1182.076312] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[ 1182.076317] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 1182.076320] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[ 1182.076323] usb 1-6: Manufacturer: Microsoft
[ 1182.080804] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.0009/input/input25
[ 1182.140510] hid-generic 0003:045E:0040.0009: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0
... snip ...
[ 3073.457826] usb 1-6: USB disconnect, device number 106
[ 3073.852405] usb 1-6: new low-speed USB device number 107 using xhci_hcd
[ 3074.000592] usb 1-6: device descriptor read/all, error -71
[ 3075.032456] usb 1-6: new low-speed USB device number 108 using xhci_hcd
[ 3075.185133] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[ 3075.185138] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 3075.185142] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[ 3075.185145] usb 1-6: Manufacturer: Microsoft
[ 3075.186768] usbhid 1-6:1.0: can't add hid device: -71
[ 3075.186802] usbhid: probe of 1-6:1.0 failed with error -71
[ 3075.186979] usb 1-6: USB disconnect, device number 108
[ 3077.368393] usb usb1-port6: Cannot enable. Maybe the USB cable is bad?
[ 3078.396352] usb 1-6: new low-speed USB device number 110 using xhci_hcd
[ 3078.549370] usb 1-6: New USB device found, idVendor=045e, idProduct=0040
[ 3078.549376] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 3078.549379] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[ 3078.549382] usb 1-6: Manufacturer: Microsoft
[ 3078.552647] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:045E:0040.005E/input/input110
[ 3078.613211] hid-generic 0003:045E:0040.005E: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-6/input0


```

---

### Post by CatKiller on 2019-11-17
Have you tried a different mouse? There are all sorts of things, from powersaving to iffy wiring, that could cause that issue.

---

### Post by Autodave on 2019-11-17
A weak power supply will do that.  If you have other USB peripherals plugged in, disconnect all of them and see what happens.  Also, if you happen to have an old style mouse (the one with the roller ball instead of a laser), try that.  Lastly, if you have access to a powered USB hub, give that a try.  

If any of my suggestions fix your issue, then it is time for a new power supply.

---

### Post by wonger33 on 2019-11-17
Yes, I've tried another mouse and it does the same thing.

---

### Post by wonger33 on 2019-11-17
The only USB devices attached are my mouse and keyboard.  
I disconnect the keyboard and the problem still occurs.  
I also tried a powered USB hub and the problem still occurs.  
Thanks for your suggestions.

---

### Post by wonger33 on 2019-11-17
I think I have some hardware problem.  I tried an Ubuntu 19.10 live CD and this problem still occurs.  But most telling is that the mouse stutters and lags when I'm in my BIOS as well.  No logs there to tell me anything, but the mouse has the same stuttering and lagging symptoms.

---

### Post by CatKiller on 2019-11-17
It definitely sounds like a hardware issue, since it's happening with multiple mice and when there's no OS.

One thing to consider is that older USB 2 devices, like keyboards and mice, often don't work properly in USB 3. I'm not exactly sure why. I don't know if that's applicable to your situation, nor if the ports you tried are of different generations. There may also be options in your BIOS to control the signalling that's used for USB devices; they'll likely refer to EHCI and xHCI.

---

### Post by wonger33 on 2019-11-17
I did try USB2 and USB3 ports.  Same issue.  But one thing I don't understand is why only mice if the USB hardware is the problem?  My USB keyboard is fine.

---

### Post by jimmyrus on 2019-11-18
> **wonger33 said:**
> I did try USB2 and USB3 ports.  Same issue.  But one thing I don't understand is why only mice if the USB hardware is the problem?  My USB keyboard is fine.
Could be just power draw since you have more than 1 usb device. Like was said, your power supply could be dodgy. Simple test would be to unplug your keyboard next time and see if your mouse stops stuttering since the voltage on the usb bus wouldn't be drawn so much. Could also try a wireless keyboard & mouse with one small dongle and see if the problem goes away.

---

### Post by wonger33 on 2019-11-23
iiiirrrrrg, problem turned out to be the mouse after all. I had TWO defective mice.  What are the odds?  A third one is working fine.  arrgh.

---

### Post by Skaperen on 2019-11-23
i've found that most mice go bad in about a year because they are so cheap.  but, for my latest replacement, i bought a very cheap one, wireless for only $12.  if i have to buy another one in a year, that's not so bad.  this one even has a nice feature: it turns itself off after 10 minutes of inactivity.  clicking any button turns it on.  2 months and it is still working on the original battery.

---

### Post by him610 on 2019-11-23
I have completely switched over to Logitech wireless mice (M185, M325, M325c, M317c)  with Logitech USB Receiver - no bluetooth. No issues. Don't even have a wired mouse anymore.

---

