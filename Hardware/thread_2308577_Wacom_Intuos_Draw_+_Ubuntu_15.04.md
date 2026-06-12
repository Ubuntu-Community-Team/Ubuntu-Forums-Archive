---
title: "Wacom Intuos Draw + Ubuntu 15.04"
date: 2016-01-04
forum: Hardware
---

### Post by marrybat on 2016-01-04
Hi, 

I bought a Wacom Intuous Draw and I cannot connect properly it to my Ubuntu 15.04. 

Wacom settings show "No tablet detected". 
But actually: 

```

> lsusb | grep Wacom
Bus 001 Device 007: ID 056a:033b Wacom Co., Ltd 

```

```

> dmesg | grep Wacom
[ 1706.283145] usb 1-9: Manufacturer: Wacom Co.,Ltd.
[ 1706.297349] input: Wacom Intuos S 2 Pen as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:056A:033B.0003/input/input26
[ 1706.351019] wacom 0003:056A:033B.0003: hidraw2: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PS] on usb-0000:00:14.0-9/input0
[ 1706.353955] input: Wacom Intuos S 2 Pad as /devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:056A:033B.0004/input/input31
[ 1706.354148] wacom 0003:056A:033B.0004: hidraw3: USB HID v1.10 Device [Wacom Co.,Ltd. Intuos PS] on usb-0000:00:14.0-9/input1
[ 2439.468356] usb 1-9: Manufacturer: Wacom Co.,Ltd.

```

I also noticed some errors in Xorg.0.log:

```

[  3196.593] (II) config/udev: Adding input device Wacom Intuos S 2 Pad (/dev/input/event20)
[  3196.593] (**) Wacom Intuos S 2 Pad: Applying InputClass "evdev tablet catchall"
[  3196.593] (**) Wacom Intuos S 2 Pad: Applying InputClass "Wacom USB device class"
[  3196.593] (**) Wacom Intuos S 2 Pad: Applying InputClass "Wacom class"
[  3196.593] (II) Using input driver 'wacom' for 'Wacom Intuos S 2 Pad'
[  3196.593] (**) Wacom Intuos S 2 Pad: always reports core events
[  3196.593] (**) Option "Device" "/dev/input/event20"
[  3196.648] (EE) Wacom Intuos S 2 Pad: Invalid type 'stylus' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad: Invalid type 'eraser' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad: Invalid type 'cursor' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad: Invalid type 'touch' for this device.
[  3196.648] (II) Wacom Intuos S 2 Pad: type not specified, assuming 'pad'.
[  3196.648] (II) Wacom Intuos S 2 Pad: other types will be automatically added.
[  3196.648] (II) Wacom Intuos S 2 Pad pad: hotplugging dependent devices.
[  3196.648] (EE) Wacom Intuos S 2 Pad pad: Invalid type 'stylus' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad pad: Invalid type 'eraser' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad pad: Invalid type 'cursor' for this device.
[  3196.648] (EE) Wacom Intuos S 2 Pad pad: Invalid type 'touch' for this device.
[  3196.648] (II) Wacom Intuos S 2 Pad pad: hotplugging completed.
[  3196.656] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.1/0003:056A:033B.000A/input/input49/event20"
[  3196.656] (II) XINPUT: Adding extended input device "Wacom Intuos S 2 Pad pad" (type: PAD, id 16)
[  3196.656] (**) Wacom Intuos S 2 Pad pad: (accel) keeping acceleration scheme 1
[  3196.656] (**) Wacom Intuos S 2 Pad pad: (accel) acceleration profile 0
[  3196.656] (**) Wacom Intuos S 2 Pad pad: (accel) acceleration factor: 2.000
[  3196.656] (**) Wacom Intuos S 2 Pad pad: (accel) acceleration threshold: 4
[  3196.657] (II) config/udev: Adding input device Wacom Intuos S 2 Pen (/dev/input/event19)
[  3196.657] (**) Wacom Intuos S 2 Pen: Applying InputClass "evdev tablet catchall"
[  3196.657] (**) Wacom Intuos S 2 Pen: Applying InputClass "Wacom USB device class"
[  3196.657] (**) Wacom Intuos S 2 Pen: Applying InputClass "Wacom class"
[  3196.657] (II) Using input driver 'wacom' for 'Wacom Intuos S 2 Pen'
[  3196.657] (**) Wacom Intuos S 2 Pen: always reports core events
[  3196.657] (**) Option "Device" "/dev/input/event19"
[  3196.712] (II) Wacom Intuos S 2 Pen: type not specified, assuming 'stylus'.
[  3196.712] (II) Wacom Intuos S 2 Pen: other types will be automatically added.
[  3196.712] (--) Wacom Intuos S 2 Pen stylus: using pressure threshold of 27 for button 1
[  3196.712] (--) Wacom Intuos S 2 Pen stylus: maxX=15200 maxY=9500 maxZ=2047 resX=100000 resY=100000  tilt=enabled
[  3196.712] (II) Wacom Intuos S 2 Pen stylus: hotplugging dependent devices.
[  3196.712] (EE) Wacom Intuos S 2 Pen stylus: Invalid type 'eraser' for this device.
[  3196.712] (EE) Wacom Intuos S 2 Pen stylus: Invalid type 'cursor' for this device.
[  3196.712] (EE) Wacom Intuos S 2 Pen stylus: Invalid type 'touch' for this device.
[  3196.712] (EE) Wacom Intuos S 2 Pen stylus: Invalid type 'pad' for this device.
[  3196.712] (II) Wacom Intuos S 2 Pen stylus: hotplugging completed.
[  3196.720] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:056A:033B.0009/input/input44/event19"
[  3196.720] (II) XINPUT: Adding extended input device "Wacom Intuos S 2 Pen stylus" (type: STYLUS, id 17)
[  3196.720] (**) Wacom Intuos S 2 Pen stylus: (accel) keeping acceleration scheme 1
[  3196.720] (**) Wacom Intuos S 2 Pen stylus: (accel) acceleration profile 0
[  3196.720] (**) Wacom Intuos S 2 Pen stylus: (accel) acceleration factor: 2.000
[  3196.720] (**) Wacom Intuos S 2 Pen stylus: (accel) acceleration threshold: 4

```

But I don't have enough skills to understand what they mean. 

I googled a little and tried this: 

```

> xsetwacom --list
Wacom Intuos S 2 Pad pad            id: 16    type: PAD       
Wacom Intuos S 2 Pen stylus         id: 17    type: STYLUS   

```

I suppose some configurations are missing but I don't really understand where to look and what to fix. 

Please help :(

---

### Post by marrybat on 2016-01-04
One remark: my device is not working at all. In the same moment as I am trying to use it, my mouse stops working and all system is seems to hang on.

---

