---
title: "Logitech G5 Stops working after upgrade to Hardy Heron 8.04"
date: 2008-04-25
forum: Hardware
---

### Post by RiazM on 2008-04-25
What's up kids, this happened to me, I think because I'd set up my mouse to be able to use the side button. Anyway, to get it working again I just opened my Xorg.conf, found the part of it that said:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB Gaming Mouse"
    Option         "Buttons" "8"
    Option         "ZAxisMapping" "4 5 7 8"
EndSection
```

and replaced it with

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection
```

This got the mouse working again, though hitting middle mouse no longer does the scroll thing in firefox. Still, its better than no mouse at all.

---

### Post by Naegling23 on 2008-04-25
Ive got the same problem....so, your fix with get the mouse working, but then it will only be a standard 3 button mouse.  Any fix to getting all the buttons working again?

---

### Post by MeanEYE on 2008-04-25
> **Naegling23 said:**
> Ive got the same problem....so, your fix with get the mouse working, but then it will only be a standard 3 button mouse.  Any fix to getting all the buttons working again?

Emulate3Buttons should mean that pressing button1 and button2 at the same time will produce click of button3 :). At least it used to be like that long time ago :) while there were no mouses with 3 buttons :)

Ouh yeah, you might wanna try lomoco [[http://lomoco.linux-gamers.net]](http://lomoco.linux-gamers.net]) it's a LOgitech MOuse COntrol. Rather old thingie.

---

### Post by roboters on 2008-04-25
add one line to your xorg.conf like this

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB Gaming Mouse"
    [COLOR="Red"]Option         "Device"	"/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"[/COLOR]
    Option         "Buttons" "8"
    Option         "ZAxisMapping" "4 5 7 8"
EndSection


```

change the device  "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse" if needed

Good luck

---

### Post by Sal Paradise on 2008-04-26
To be more precise, /dev/input/by-id contains a list of soft links to your input devices. For example, on my system, the links were:

[INDENT]bob@GA3800:/dev/input/by-id$ ls -l
total 0
lrwxrwxrwx 1 root root 9 2008-04-26 16:46 usb-BTC_USB_Multimedia_Keyboard-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-04-26 16:46 usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2008-04-26 16:46 usb-Logitech_USB-PS.2_Optical_Mouse-mouse -> ../mouse1
[/INDENT]

So in my file, to get the mouse working again, I added this line:

[INDENT]Option	"Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical _Mouse-event-mouse"[/INDENT]

BTW, the xorg.conf file is in the /etc/X11 directory, and is owned by root., so you need something like:
[INDENT] sudo gedit /etc/X11/xorg.conf[/INDENT]
to edit it.

---

### Post by Naegling23 on 2008-04-28
roboters, tried yours, didnt work.

All I did was change the mouse driver from evdev to mouse....all works fine now.  I think it was evdev because there was something not complete about the standard mouse driver, seems to be updated, and no more need for evdev, so it was eliminated?

---

### Post by chuck2 on 2008-05-01
edit: seems like the community moves fast, yesterday I couldn't find useful info, so I started experimenting, so did other people. heres what some guy did, it works for me:

in the xorg.conf:
```

Section “InputDevice”
Identifier “Logitech G5&#8243;
Driver “evdev”
Option “CorePointer”
Option “Device” “/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse”
Option “ZAxisMapping” “invert”
Option “Emulate3Buttons” “false”
Option “Buttons” “9&#8243;
Option “Resolution” “800&#8243;
EndSection

```


in the .Xmodmap:
```

pointer = 1 2 3 4 5 9 8 6 7

```

---

