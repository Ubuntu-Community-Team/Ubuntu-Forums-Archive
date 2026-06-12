---
title: "ThinkPad Keyboard + USB Hub = No Trackpoint"
date: 2014-08-10
forum: Hardware
---

### Post by eprst on 2014-08-10
Hi

I'm having issues with Lenovo ThinkPad Keyboard with integrated Trackpoint. It works fine when connected directly into PC, but trackpoint doesn't work when connected via USB hub. Keys still work fine.

Kernel: 3.13.0-32-generic

dmesg (when connected via hub):
```
[  507.778703] usb 2-2.5: new low-speed USB device number 9 using xhci_hcd
[  507.804906] usb 2-2.5: New USB device found, idVendor=17ef, idProduct=6009
[  507.804916] usb 2-2.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  507.804920] usb 2-2.5: Product: ThinkPad USB Keyboard with TrackPoint
[  507.804924] usb 2-2.5: Manufacturer: Lite-On Technology Corp.
[  507.805198] usb 2-2.5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  507.805209] usb 2-2.5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[  507.809680] input: Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.5/2-2.5:1.0/input/input16
[  507.809975] lenovo_tpkbd 0003:17EF:6009.0009: input,hidraw2: USB HID v1.10 Keyboard [Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint] on usb-0000:00:14.0-2.5/input0
[  507.819465] input: Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2.5/2-2.5:1.1/input/input17
[  507.820294] lenovo_tpkbd 0003:17EF:6009.000A: input,hiddev0,hidraw3: USB HID v1.10 Mouse [Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint] on usb-0000:00:14.0-2.5/input1
```

"xinput list" output: 
```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; RCMCU 2.4GHz receiver                     id=10   [slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint    id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; RCMCU 2.4GHz receiver                     id=9    [slave  keyboard (3)]
    &#8627; Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint    id=12   [slave  keyboard (3)]
```

"xinput list-props 11":
```

Device 'Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint':
        Device Enabled (129):   1
        Coordinate Transformation Matrix (131): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (250):     0
        Device Accel Constant Deceleration (251):       1.000000
        Device Accel Adaptive Deceleration (252):       1.000000
        Device Accel Velocity Scaling (253):    10.000000
        Device Product ID (246):        6127, 24585
        Device Node (247):      "/dev/input/event10"
        Evdev Axis Inversion (254):     0, 0
        Evdev Axes Swap (256):  0
        Axis Labels (257):      "Rel X" (139), "Rel Y" (140)
        Button Labels (258):    "Button Left" (132), "Button Middle" (133), "Button Right" (134), "Button Wheel Up" (135), "Button Wheel Down" (136), "Button Horiz Wheel Left" (137), "Button Horiz Wheel Right" (138), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249), "Button Unknown" (249)
        Evdev Middle Button Emulation (259):    1
        Evdev Middle Button Timeout (260):      50
        Evdev Third Button Emulation (261):     0
        Evdev Third Button Emulation Timeout (262):     1000
        Evdev Third Button Emulation Button (263):      3
        Evdev Third Button Emulation Threshold (264):   20
        Evdev Wheel Emulation (265):    1
        Evdev Wheel Emulation Axes (266):       6, 7, 4, 5
        Evdev Wheel Emulation Inertia (267):    10
        Evdev Wheel Emulation Timeout (268):    200
        Evdev Wheel Emulation Button (269):     2
        Evdev Drag Lock Buttons (270):  0
```

there's no output from "cat /dev/input/event10" when trackpoint is used. Kernel bug?

---

### Post by tgalati4 on 2014-08-11
Not all USB hubs are created equal.  Does your hub have a power socket?  If so, find a power supply to power it.  Go to a computer store and ask to try different hubs in the store.  Or find a neighbor or Linux User Group (LUG) in your area and ask around for USB hubs to test.  It's possible the hub is not providing enough power to "wake up" the TrackPoint circuitry or the hub circuitry is not providing the correct timing.

> [  507.805198] usb 2-2.5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes

Understand that the hub draws power as well as the keyboard, so if the combination exceed 500 mAmps, you will get an overcurrent condition which the USB module will react to.

A google search on "rounding interval to 64 microframes"

[http://unix.stackexchange.com/questions/132266/usb-device-messages-flooding-dmesg-and-console](http://unix.stackexchange.com/questions/132266/usb-device-messages-flooding-dmesg-and-console)  Possible lack of USB power.

---

### Post by eprst on 2014-08-11
thanks for the ideas
this is a powered USB hub.. may be just some weird incompatibility indeed

---

