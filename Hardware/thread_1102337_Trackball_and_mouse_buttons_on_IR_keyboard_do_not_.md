---
title: "Trackball and mouse buttons on IR keyboard do not work"
date: 2009-03-21
forum: Hardware
---

### Post by Surkow on 2009-03-21
I was originally planning to post in [this]("http://ubuntuforums.org/showthread.php?t=168827") thread. Since it was archived I had to create a new thread about my issue with an old IR keyboard with a trackball and mouse buttons on top. Currently the keyboard works properly. I have been unable to get the trackball and mouse buttons to work. It's a generic server IR keyboard without a brand name.

"[FONT="Courier New"]$cat /var/log/messages[/FONT]" gives me:

```
Mar 21 19:10:33 desktop kernel: [33640.625202] usb 2-5: new low speed USB device using ohci_hcd and address 8
Mar 21 19:10:33 desktop kernel: [33640.842467] usb 2-5: configuration #1 chosen from 1 choice
Mar 21 19:10:33 desktop kernel: [33640.855444] input: JME Co., Ltd. USB Wireless Controller as /class/input/input14
Mar 21 19:10:33 desktop kernel: [33640.855467] input: USB HID v1.00 Keyboard [JME Co., Ltd. USB Wireless Controller] on usb-0000:00:0b.0-5
Mar 21 19:10:33 desktop kernel: [33640.868428] input: JME Co., Ltd. USB Wireless Controller as /class/input/input15
Mar 21 19:10:33 desktop kernel: [33640.868447] input: USB HID v1.00 Mouse [JME Co., Ltd. USB Wireless Controller] on usb-0000:00:0b.0-5
```

More information can be found in [this]("http://aaltonen.us/2005/08/26/logitech-mx1000-under-ubuntu/") tutorial about getting a Logitech device to work. It suggests to search for a "Dev Phys" property to be used in xorg.conf. Like for example:

```
Section "InputDevice"
    Identifier "Logitech MX1000"
    Driver "mouse"
    Option "Protocol" "evdev"
    Option "Dev Name" "Logitech USB Receiver"
    Option "Dev Phys" "usb-0000:00:02.0-4/input0"
    Option "Device" "/dev/input/mice"
    Option "Buttons" "12"
    Option "ZAxisMapping" "4 5"
    Option "Resolution" "800"
    Option "CorePointer"
EndSection
```

To get the "Dev Phys" property I did the following:

```
$cat /proc/bus/input/devices | grep -A1 "less"
N: Name="JME Co., Ltd. USB Wireless Controller"
P: Phys=usb-0000:00:0b.0-5/input0
--
N: Name="JME Co., Ltd. USB Wireless Controller"
P: Phys=usb-0000:00:0b.0-5/input1
```

And I added the following information to "[FONT="Courier New"]/etc/X11/xorg.conf[/FONT]":

```
Section "InputDevice"
    Identifier "IR Mouse"
    Driver "mouse"
    Option "Protocol" "evdev"
    Option "Dev Phys" "usb-0000:00:0b.0-5/input0"
    Option "Device" "/dev/input/mice"
    Option "Buttons" "12"
    Option "ZAxisMapping" "4 5"
    Option "CorePointer"
EndSection
```

No working trackball or mouse buttons after restarting X. Any suggestions? I already tried "[FONT="Courier New"]input1[/FONT]"

---

### Post by Surkow on 2009-03-22
Bump. I guess this is not a common question. ;)

---

