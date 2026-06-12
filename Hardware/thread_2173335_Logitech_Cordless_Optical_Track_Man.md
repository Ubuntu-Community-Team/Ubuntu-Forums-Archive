---
title: "Logitech Cordless Optical Track Man"
date: 2013-09-09
forum: Hardware
---

### Post by johnaaronrose on 2013-09-09
I've just brought out of the cupboard a Logitech Cordless Optical Track Man. It's not been used since I was using 10.04, when it worked OK. I'm now using 12.04. It doesn't work at all now. 

    lsusb shows:
    Bus 002 Device 011: ID 046d:c508 Logitech, Inc. Cordless Trackball
    
    dmesg|grep Logitech shows:
    [27065.831759] usb 2-1.6.7.2: Manufacturer: Logitech
    [27065.836101] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.7/2-1.6.7.2/2-1.6.7.2:1.0/input/input12
    [27065.836354] hid-generic 0003:046D:C508.0004: input,hidraw3: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.6.7.2/input0
    
    tail -f /var/log/Xorg.0.log shows:
    [ 27106.064] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
    [ 27106.064] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
    [ 27106.064] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
    [ 27106.064] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.7/2-1.6.7.2/2-1.6.7.2:1.0/input/input12/event12"
    [ 27106.064] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 13)
    [ 27106.064] (II) evdev: Logitech USB Receiver: initialized for relative axes.
    [ 27106.064] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
    [ 27106.064] (**) Logitech USB Receiver: (accel) acceleration profile 0
    [ 27106.064] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
    [ 27106.064] (**) Logitech USB Receiver: (accel) acceleration threshold: 4

Any ideas?

---

### Post by Bucky Ball on 2013-09-09
Posted in error. Apologies.

---

### Post by johnaaronrose on 2013-09-09
I'm stupid. I replaced the batteries and it was OK.

---

### Post by Bucky Ball on 2013-09-09
Ha! Not as stupid as me!!! The post above I deleted read:

'I know this might sound dumb and obvious, but does it use batteries and if so, has the battery got any charge left?'

LOL. I got it right in the first place. Should have left that post up! Haha. 

Anyhow, could you mark the thread as solved to help others using Thread Tools at top right.
 
Enjoy! ;)

---

