---
title: "Logitech Wireless Mouse not working"
date: 2008-07-31
forum: Hardware
---

### Post by drh004 on 2008-07-31
The mouse is a Logitech Wireless mini optical mouse. when i plug in the usb reciever the mouse does nothing.  I attempted to follow this guide to get it working:

[http://http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+wireless+mini+optical+mouse]("http://http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+wireless+mini+optical+mouse")

when i use the command:
```
cat /proc/bus/input/devices
``` 
in the terminal the mouse is not listed

this is the result of that command
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1004 2200001 c3803078 f910d401 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

``` 

however when i use the command:
```
dmesg|grep usb
```
the mouse shows up

```
[   22.242563] usbcore: registered new interface driver usbfs
[   22.242588] usbcore: registered new interface driver hub
[   22.242826] usbcore: registered new device driver usb
[   22.302714] usb usb1: configuration #1 chosen from 1 choice
[   22.462438] usb usb2: configuration #1 chosen from 1 choice
[   22.712578] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   22.928666] usb 1-4: configuration #1 chosen from 1 choice
[   23.235045] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   23.247137] usb usb3: configuration #1 chosen from 1 choice
[   23.422835] usb usb4: configuration #1 chosen from 1 choice
[   23.822697] usb 2-2: device not accepting address 2, error -62
[   23.878621] usb 1-4: USB disconnect, address 2
[   23.878778] usbcore: registered new interface driver hiddev
[   24.593407] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   24.742526] usb 4-2: configuration #1 chosen from 1 choice
[   24.742788] usbcore: registered new interface driver usbhid
[   24.742791] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.044653] usb 1-4: new low speed USB device using ohci_hcd and address 3
[   25.273402] usb 1-4: configuration #1 chosen from 1 choice
[   25.287494] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input2
[   25.312274] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-4
[   41.253668] usbcore: registered new interface driver lmpcm_usb
[   41.253674] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   41.450153] usbcore: registered new interface driver uvcvideo
[   42.798961] usbcore: registered new interface driver ndiswrapper
[  133.881902] usb usb2: USB disconnect, address 1
[  133.882190] usb usb1: USB disconnect, address 1
[  133.882192] usb 1-4: USB disconnect, address 3
[  133.940035] usbcore: deregistering interface driver ndiswrapper
[  134.388123] usbcore: registered new interface driver ndiswrapper
root@laptop:/home/dustn# dmesg|grep usb
[   22.242563] usbcore: registered new interface driver usbfs
[   22.242588] usbcore: registered new interface driver hub
[   22.242826] usbcore: registered new device driver usb
[   22.302714] usb usb1: configuration #1 chosen from 1 choice
[   22.462438] usb usb2: configuration #1 chosen from 1 choice
[   22.712578] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   22.928666] usb 1-4: configuration #1 chosen from 1 choice
[   23.235045] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   23.247137] usb usb3: configuration #1 chosen from 1 choice
[   23.422835] usb usb4: configuration #1 chosen from 1 choice
[   23.822697] usb 2-2: device not accepting address 2, error -62
[   23.878621] usb 1-4: USB disconnect, address 2
[   23.878778] usbcore: registered new interface driver hiddev
[   24.593407] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   24.742526] usb 4-2: configuration #1 chosen from 1 choice
[   24.742788] usbcore: registered new interface driver usbhid
[   24.742791] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.044653] usb 1-4: new low speed USB device using ohci_hcd and address 3
[   25.273402] usb 1-4: configuration #1 chosen from 1 choice
[   25.287494] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input2
[   25.312274] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-4
[   41.253668] usbcore: registered new interface driver lmpcm_usb
[   41.253674] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   41.450153] usbcore: registered new interface driver uvcvideo
[   42.798961] usbcore: registered new interface driver ndiswrapper
[  133.881902] usb usb2: USB disconnect, address 1
[  133.882190] usb usb1: USB disconnect, address 1
[  133.882192] usb 1-4: USB disconnect, address 3
[  133.940035] usbcore: deregistering interface driver ndiswrapper
[  134.388123] usbcore: registered new interface driver ndiswrapper
```

does anyone have any idea why the mouse is not working?

---

