---
title: "USB Gamepad (DDR Pad) Buttons Not Working"
date: 2009-08-26
forum: Hardware
---

### Post by wall0645 on 2009-08-26
Hi I'm trying to get my USB DDR pad working in Ubuntu Jaunty 9.04.

This same pad worked fine in Ubuntu Hardy 8.04 on a Sony VAIO laptop, but doesn't seem to work on this Lenovo ThinkPad (R61i).

Here is what lsusb says:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 045e:0285 Microsoft Corp. Xbox Controller S
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```As you can see it says it is an Xbox Controller (this is actually not true, it is a [BNS DX Xtreme Fusion]("http://www.buynshop.com/productinfo/4985/VG-DDR-ULTDX/"). It does have XBOX and PS2 connectors as well as USB, but I'm using the USB).

Here is what the log says when I plug it in and unplug it:
> ...
Aug 26 18:30:08 nick-laptop pulseaudio[3444]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 26 18:30:08 nick-laptop pulseaudio[3444]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
****PLUG IN PAD***
Aug 26 18:46:16 nick-laptop kernel: [ 1028.552098] usb 5-1: new low speed USB device using uhci_hcd and address 2
Aug 26 18:46:16 nick-laptop kernel: [ 1028.766347] usb 5-1: configuration #1 chosen from 1 choice
Aug 26 18:46:16 nick-laptop kernel: [ 1028.888290] usbcore: registered new interface driver hiddev
Aug 26 18:46:17 nick-laptop kernel: [ 1028.904354] input: HID 045e:0285 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input9
Aug 26 18:46:17 nick-laptop kernel: [ 1028.905847] generic-usb 0003:045E:0285.0001: input,hidraw0: USB HID v1.00 Joystick [HID 045e:0285] on usb-0000:00:1d.0-1/input0
Aug 26 18:46:17 nick-laptop kernel: [ 1028.905888] usbcore: registered new interface driver usbhid
Aug 26 18:46:17 nick-laptop kernel: [ 1028.905895] usbhid: v2.6:USB HID core driver
***UNPLUG PAD***
Aug 26 18:48:08 nick-laptop kernel: [ 1140.472191] usb 5-1: USB disconnect, address 2

The pad is listed as js0 in /dev/input. Nothing shows up when I use xev and hit the buttons.

I'm really unsure as to what to do to get this working. Any ideas? Thanks in advance! :)

---

### Post by wall0645 on 2009-08-26
Turns out I just needed to install the drivers, lol. These are the ones:
xserver-xorg-input-joystick
joystick

Hopefully this helps somebody out there! :)

---

