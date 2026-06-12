---
title: "USB Camera issues, listing multiple times in inputs"
date: 2011-02-17
forum: Hardware
---

### Post by binary.nation on 2011-02-17
Alright everyone, when I try using my Logitech Quickcam Pro using an extension cable or hub I get a blank screen. Everytime I unplug it and plug it back in it adds a new listing to:

/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2.1/1-2.1:1.0/input/

Here's the output of lsusb
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 025: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 001 Device 018: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 007: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 001 Device 005: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 001 Device 002: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and here's the output of dmesg | grep 046d:0991
> [83175.482596] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[83175.524624] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input10
[83239.766406] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[83239.809654] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3.2/1-3.2:1.0/input/input11
[84361.501290] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[84361.545589] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2.1/1-2.1:1.0/input/input14
[861263.563753] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[861263.605937] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input15
[861731.811268] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[861731.853512] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input16
[862177.585367] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[862177.627085] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input17
[947841.571245] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[947841.621427] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input18
[949968.282552] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[949968.324700] input: UVC Camera (046d:0991) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input19

So why's my camera not working?

---

