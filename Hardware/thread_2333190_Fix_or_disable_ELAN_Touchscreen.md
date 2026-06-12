---
title: "Fix or disable ELAN Touchscreen"
date: 2016-08-07
forum: Hardware
---

### Post by kevinkhill on 2016-08-07
Hello everyone! Long time ubuntu user, but first time poster here. I need help as I have exhausted my google-fu and can't seem to figure this out.

I have a Toshiba Satelite Radius P55W-B5224 that I installed Ubuntu on (I later installed xubuntu-desktop, xfce-desktop?) and I am having this strange issue with the touchscreen. It appears through dmesg that I am rapidly plugging and unplugging it, and I am wondering if that is interfering with my flash-drives automounting (but that's a different issue for a different post)

I would love either a fix for the touchscreen so it works, or just blacklist/disable it so it's not flooding the system. (I don't really care if it works or not).

It looks like it starts as device 1 and goes until device 127, then loops... I don't know how to be anymore helpful than post a piece of the dmesg output:

```

[19729.743314] usb 2-4: new full-speed USB device number 58 using xhci_hcd
[19729.872960] usb 2-4: New USB device found, idVendor=04f3, idProduct=0381
[19729.872964] usb 2-4: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[19729.872966] usb 2-4: Product: Touchscreen
[19729.872968] usb 2-4: Manufacturer: ELAN
[19729.873129] usb 2-4: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[19729.882170] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/0003:04F3:0381.70A9/input/input57665
[19729.882435] hid-multitouch 0003:04F3:0381.70A9: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-4/input0
[19729.892868] usb 2-4: USB disconnect, device number 58
[19730.171287] usb 2-4: new full-speed USB device number 59 using xhci_hcd
[19730.300890] usb 2-4: New USB device found, idVendor=04f3, idProduct=0381
[19730.300894] usb 2-4: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[19730.300896] usb 2-4: Product: Touchscreen
[19730.300898] usb 2-4: Manufacturer: ELAN
[19730.301055] usb 2-4: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[19730.310163] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/0003:04F3:0381.70AA/input/input57667
[19730.310493] hid-multitouch 0003:04F3:0381.70AA: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-4/input0
[19730.320996] usb 2-4: USB disconnect, device number 59
[19730.603279] usb 2-4: new full-speed USB device number 60 using xhci_hcd
[19730.732864] usb 2-4: New USB device found, idVendor=04f3, idProduct=0381
[19730.732869] usb 2-4: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[19730.732871] usb 2-4: Product: Touchscreen
[19730.732874] usb 2-4: Manufacturer: ELAN
[19730.733018] usb 2-4: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[19730.742134] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/0003:04F3:0381.70AB/input/input57669
[19730.742380] hid-multitouch 0003:04F3:0381.70AB: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-4/input0
[19730.753480] usb 2-4: USB disconnect, device number 60
[19731.023249] usb 2-4: new full-speed USB device number 61 using xhci_hcd
[19731.156953] usb 2-4: New USB device found, idVendor=04f3, idProduct=0381
[19731.156957] usb 2-4: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[19731.156958] usb 2-4: Product: Touchscreen
[19731.156959] usb 2-4: Manufacturer: ELAN
[19731.157098] usb 2-4: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[19731.166144] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/0003:04F3:0381.70AC/input/input57671
[19731.166443] hid-multitouch 0003:04F3:0381.70AC: input,hiddev0,hidraw0: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-4/input0
[19731.177365] usb 2-4: USB disconnect, device number 61

```

Thank you in advance for taking time to help, if you can :)

---

