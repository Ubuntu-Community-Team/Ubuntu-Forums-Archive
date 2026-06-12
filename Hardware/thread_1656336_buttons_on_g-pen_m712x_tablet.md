---
title: "buttons on g-pen m712x tablet"
date: 2010-12-30
forum: Hardware
---

### Post by kolage on 2010-12-30
Hi everyone,

I have such a problem with my tablet in Ubuntu 10.10. Everything works fine except the buttons on the pad and I really don't know how to figure it out ... I tried xev if it output something when i press the keys with pen, but nothing. I would be really grateful to anyone with some idea...

dmesg output :
```

[  287.856026] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  288.109909] usbcore: registered new interface driver hiddev
[  288.125329] input: WALTOP International Corp. Media Tablet as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input4
[  288.125676] generic-usb 0003:172F:0500.0001: input,hidraw0: USB HID v1.10 Mouse [WALTOP International Corp. Media Tablet] on usb-0000:00:10.0-2/input0
[  288.126921] usbcore: registered new interface driver usbhid
[  288.126928] usbhid: USB HID core driver

```

I use wacom driver, here is 50-wacom.conf :
```

Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
	MatchProduct "Wacom|WALTOP|WACOM"
#	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

```

And here is the picture of tablet : [http://www.hitechreview.com/uploads/2009/08/Genius-G-Pen-M712X.jpg](http://www.hitechreview.com/uploads/2009/08/Genius-G-Pen-M712X.jpg)

---

