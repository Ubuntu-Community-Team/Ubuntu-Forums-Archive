---
title: "webcam sometimes not recognized"
date: 2020-12-11
forum: Hardware
---

### Post by loverdrive on 2020-12-11
Hi,
i have a logitech webcam (C310 HD model). I used it some days and it worked very well. In last 2 days i have some problems. When i start a videocall (or just open cheese) it works but after a few seconds it stop working, no more video/audio displayed/played. Sometimes after a few second it start working again, but then stop again.

I attach log of dmesg -wH

```

[dic11 16:21] usb 3-3: reset high-speed USB device number 6 using xhci_hcd
[ +29,033655] usb 3-3: USB disconnect, device number 6
[  +0,002606] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003986] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004003] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003997] uvcvideo: Failed to resubmit video URB (-19).
[  +0,342958] usb 3-3: new high-speed USB device number 7 using xhci_hcd
[  +0,368681] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,028304] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039288] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input18
[  +1,209151] usb 3-3: set resolution quirk: cval->res = 384
[  +7,078530] usb 3-3: USB disconnect, device number 7
[  +0,000984] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003984] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003998] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,334982] usb 3-3: new high-speed USB device number 8 using xhci_hcd
[  +0,467655] usb 3-3: unable to read config index 0 descriptor/all
[  +0,000005] usb 3-3: can't read configurations, error -71
[  +0,540336] usb 3-3: new high-speed USB device number 9 using xhci_hcd
[  +0,572661] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000004] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,028429] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039568] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input19
[  +1,208749] usb 3-3: set resolution quirk: cval->res = 384
[dic11 16:22] usb 3-3: USB disconnect, device number 9
[  +0,003477] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003992] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +1,094488] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,899997] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,000028] usb usb3-port3: attempt power cycle
[  +0,859942] usb 3-3: new high-speed USB device number 12 using xhci_hcd
[  +0,243063] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,022424] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039348] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input20
[  +1,209093] usb 3-3: set resolution quirk: cval->res = 384
[dic11 16:26] usb 3-3: USB disconnect, device number 12
[  +0,003096] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003991] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004001] uvcvideo: Failed to resubmit video URB (-19).
[  +0,308198] usb 3-3: new high-speed USB device number 13 using xhci_hcd
[  +0,900006] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,543972] usb 3-3: new high-speed USB device number 14 using xhci_hcd
[  +0,364587] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000001] usb 3-3: SerialNumber: 39A270A0
[  +0,031307] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039470] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input21
[  +1,208967] usb 3-3: set resolution quirk: cval->res = 384
[  +1,238376] retire_capture_urb: 26 callbacks suppressed
[  +0,000026] usb 3-3: USB disconnect, device number 14
[  +0,000968] usb 3-3: cannot submit urb (err = -19)
[  +0,000055] usb 3-3: cannot submit urb 0, error -19: no device
[  +0,000081] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003988] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,328135] usb 3-3: new high-speed USB device number 15 using xhci_hcd
[  +0,364645] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,019301] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039493] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input22
[  +1,209412] usb 3-3: set resolution quirk: cval->res = 384
[  +1,383416] usb 3-3: USB disconnect, device number 15
[  +0,000473] usb 3-3: cannot submit urb (err = -19)
[  +0,000064] usb 3-3: cannot submit urb 0, error -19: no device
[  +0,003067] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003993] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,332102] usb 3-3: new high-speed USB device number 16 using xhci_hcd
[  +0,376784] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,031173] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039085] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input23
[  +1,209236] usb 3-3: set resolution quirk: cval->res = 384
[  +1,405397] usb 3-3: USB disconnect, device number 16
[  +0,000132] usb 3-3: cannot submit urb (err = -19)
[  +0,000065] usb 3-3: cannot submit urb 0, error -19: no device
[  +0,002038] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003987] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,304066] usb 3-3: new high-speed USB device number 17 using xhci_hcd
[  +0,364698] usb 3-3: New USB device found, idVendor=046d, idProduct=081b, bcdDevice= 0.10
[  +0,000003] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[  +0,000002] usb 3-3: SerialNumber: 39A270A0
[  +0,019301] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[  +0,039609] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:08.1/0000:0b:00.3/usb3/3-3/3-3:1.0/input/input24
[  +1,208976] usb 3-3: set resolution quirk: cval->res = 384
[  +1,371261] usb 3-3: USB disconnect, device number 17
[  +0,000123] uvcvideo: Failed to resubmit video URB (-19).
[  +0,000842] usb 3-3: cannot submit urb (err = -19)
[  +0,000067] usb 3-3: cannot submit urb 0, error -19: no device
[  +0,003055] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004000] uvcvideo: Failed to resubmit video URB (-19).
[  +0,003999] uvcvideo: Failed to resubmit video URB (-19).
[  +0,004001] uvcvideo: Failed to resubmit video URB (-19).
[  +1,104042] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,899990] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,000032] usb usb3-port3: attempt power cycle
[  +1,219977] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,903972] usb usb3-port3: Cannot enable. Maybe the USB cable is bad?
[  +0,000033] usb usb3-port3: unable to enumerate USB device


```

It could be an hardware problem? Usb cable is well connected.

Thank you

---

### Post by Kirboosy on 2020-12-15
Welcome to the forums!

Could you run the following command and paste the output here?
```
lsusb
```

The webcam cable could be frayed internally, but if the webcam works flawlessly on other systems then that would rule out that issue.

Which version of Ubuntu are you running? I would also suggest trying a LiveCD of Ubuntu 20.04 to verify it's not a configuration on your system. It should "just work" out of the box.

---

