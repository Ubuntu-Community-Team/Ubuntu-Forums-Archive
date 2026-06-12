---
title: "TOUCH SCREEN resolution"
date: 2013-01-17
forum: Hardware
---

### Post by yurkomik on 2013-01-17
Hello. I think it's easy question but I can't find easy unswer.
I have laptop with kubuntu 12.10 and 1280*720 native resolution. Connected it to external HD monitor 1920*1280 resolution and IR touchscreen from WiViTouch. 
dmesg output:
> usb 2-2: new full-speed USB device number 16 using uhci_hcd
[ 1816.566202] usb 2-2: New USB device found, idVendor=04b4, idProduct=c001
[ 1816.566212] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1816.566219] usb 2-2: Product: Touch  Computer INC.
[ 1816.566225] usb 2-2: Manufacturer: Touch__KiT
[ 1816.594428] input: Touch__KiT Touch  Computer INC. as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input10
[ 1816.594759] hid-multitouch 0003:04B4:C001.0003: input,hiddev0,hidraw0: USB HID v1.01 Mouse [Touch__KiT Touch  Computer INC.] on usb-0000:00:1d.0-2/input0


xorg.0.log:
> [  1375.569] (II) config/udev: Adding input device Touch__KiT Touch  Computer INC. (/dev/input/mouse1)
[  1375.569] (II) No input driver specified, ignoring this device.
[  1375.569] (II) This device may have been added with another device file.
[  1375.570] (II) config/udev: Adding input device Touch__KiT Touch  Computer INC. (/dev/input/event8)
[  1375.570] (**) Touch__KiT Touch  Computer INC.: Applying InputClass "evdev touchscreen catchall"
[  1375.570] (II) Using input driver 'evdev' for 'Touch__KiT Touch  Computer INC.'
[  1375.570] (**) Touch__KiT Touch  Computer INC.: always reports core events
[  1375.570] (**) evdev: Touch__KiT Touch  Computer INC.: Device: "/dev/input/event8"
[  1375.570] (--) evdev: Touch__KiT Touch  Computer INC.: Vendor 0x4b4 Product 0xc001
[  1375.570] (--) evdev: Touch__KiT Touch  Computer INC.: Found absolute axes
[  1375.570] (--) evdev: Touch__KiT Touch  Computer INC.: Found absolute multitouch axes
[  1375.570] (--) evdev: Touch__KiT Touch  Computer INC.: Found x and y absolute axes
[  1375.570] (--) evdev: Touch__KiT Touch  Computer INC.: Found absolute touchscreen
[  1375.570] (II) evdev: Touch__KiT Touch  Computer INC.: Configuring as touchscreen
[  1375.571] (**) evdev: Touch__KiT Touch  Computer INC.: YAxisMapping: buttons 4 and 5
[  1375.571] (**) evdev: Touch__KiT Touch  Computer INC.: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1375.571] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8/event8"
[  1375.571] (II) XINPUT: Adding extended input device "Touch__KiT Touch  Computer INC." (type: TOUCHSCREEN, id 12)
[  1375.571] (II) evdev: Touch__KiT Touch  Computer INC.: initialized for absolute axes.
[  1375.571] (**) Touch__KiT Touch  Computer INC.: (accel) keeping acceleration scheme 1
[  1375.571] (**) Touch__KiT Touch  Computer INC.: (accel) acceleration profile 0
[  1375.571] (**) Touch__KiT Touch  Computer INC.: (accel) acceleration factor: 2.000
[  1375.571] (**) Touch__KiT Touch  Computer INC.: (accel) acceleration threshold: 4

Using screen settings I've shut down internal laptop LVDS monitor and use only external one. Touchscreen works ok in 1280*720 resolution. If I try to work in Full HD it's not good at all and can't be calibrated by xinput-calibration utility.

If I press text in the centre of the screen pointer is 10 cm down from actual touch. Only on top it's in the same position. 
Can I fix it somehow? There no xorg.conf in my system even to look there. Please help!

---

### Post by yurkomik on 2013-01-17
I don't know why but next time I changed screen resolution to 1920*1280 it's somehow fixed itself ^)

---

