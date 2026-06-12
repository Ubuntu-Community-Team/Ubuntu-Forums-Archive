---
title: "Logitech USB Receiver not working, Ubuntu 16.10 [SOLVED]"
date: 2017-03-20
forum: Hardware
---

### Post by massimiliano-bellomo-s on 2017-03-20
Dear all,

i cannot get the Logitech receiver to work for the M185 wireless mouse.
The problem could be that the kernel module hid-generic is uised instead of
the hid_logitech_dj (that i loaded myself with modprobe).

I've tried already to load/unload the hid_logitech_dj module as suggested in
other threads but doesn't change anything, the generic module is always used.

Please find some details below.

best,
   Max


Ubuntu 16.10, 4.8.0-41-generic

HP EliteDesk 800 G2
[http://www.hp.com/sbso/hpinfo/newsroom/HPElitePC2015/AMSHPEliteDesk800G2TowerPCDatasheet.pdf](http://www.hp.com/sbso/hpinfo/newsroom/HPElitePC2015/AMSHPEliteDesk800G2TowerPCDatasheet.pdf)

```

dmesg
[ 4878.598389] usb 1-10: new full-speed USB device number 14 using xhci_hcd
[ 4878.742044] usb 1-10: New USB device found, idVendor=046d, idProduct=c534
[ 4878.742050] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4878.742053] usb 1-10: Product: USB Receiver
[ 4878.742056] usb 1-10: Manufacturer: Logitech
[ 4878.744674] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/0003:046D:C534.0016/input/input46
[ 4878.803095] hid-generic 0003:046D:C534.0016: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-10/input0
[ 4878.805934] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:046D:C534.0017/input/input47
[ 4878.863448] hid-generic 0003:046D:C534.0017: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-10/input1

```

```

lsusb 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 013: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

lsmod | grep usb
usbhid                 53248  0
hid                   118784  3 hid_generic,usbhid,hid_logitech_dj

```

```

solaar-cli show
solaar-cli: error: Logitech receiver not found

```

---

### Post by jeremy31 on 2017-03-20
It appears solaar doesn't support for your device but their is a pull request that could add it- [https://github.com/pwr/Solaar/pull/337/files](https://github.com/pwr/Solaar/pull/337/files)

See if the mouse shows in
```
xinput
```

---

### Post by massimiliano-bellomo-s on 2017-03-20
Thanks for the reply. 

Please find below the xinput output. 
Note that i've also a wired usb mouse plugged in
showed below at id=16.

Shouldn't the hid_logitech_dj module be used?

```

xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                       id=10    [slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                       id=11    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=12    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=14    [slave  keyboard (3)]

```

---

### Post by jeremy31 on 2017-03-20
I am not sure what driver it should use but I know it was reported to work in Ubuntu 12.04.  Did you find a post or bug report that indicates the hid-logitech-dj module needed to be used?
Post results for
```
xinput list-props 16
```

---

### Post by massimiliano-bellomo-s on 2017-03-20
Actually i'm not 100% sure that module should be used....in many others posts is mentioned such that it seems it's needed
but indeed it was not stated clearly.

Here is the output, however please note that this is the wired usb mouse, the other mouse connected.
An HP mouse curiously called Logitech USB Optical Mouse....

```

xinput list-props 16
Device 'Logitech USB Optical Mouse':
    Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Accel Speed (273):    0.000000
    libinput Accel Speed Default (274):    0.000000
    libinput Accel Profiles Available (275):    1, 1
    libinput Accel Profile Enabled (276):    1, 0
    libinput Accel Profile Enabled Default (277):    1, 0
    libinput Natural Scrolling Enabled (278):    0
    libinput Natural Scrolling Enabled Default (279):    0
    libinput Send Events Modes Available (257):    1, 0
    libinput Send Events Mode Enabled (258):    0, 0
    libinput Send Events Mode Enabled Default (259):    0, 0
    libinput Left Handed Enabled (280):    0
    libinput Left Handed Enabled Default (281):    0
    libinput Scroll Methods Available (282):    0, 0, 1
    libinput Scroll Method Enabled (283):    0, 0, 0
    libinput Scroll Method Enabled Default (284):    0, 0, 0
    libinput Button Scrolling Button (285):    2
    libinput Button Scrolling Button Default (286):    274
    libinput Middle Emulation Enabled (287):    0
    libinput Middle Emulation Enabled Default (288):    0
    Device Node (260):    "/dev/input/event8"
    Device Product ID (261):    1133, 49176
    libinput Drag Lock Buttons (289):    <no items>
    libinput Horizonal Scroll Enabled (262):    1

```

---

### Post by massimiliano-bellomo-s on 2017-03-20
oh gosh ... the battery shipped with the mouse was faulty....replacing it it worked instantly like a charm....

sorry for the noise .... and many thanks for the prompt reply.

So Logithech M185 works in Ubuntu 16.10 out of the box!

best,
  Max

---

