---
title: "turn down mouse speed"
date: 2010-04-18
forum: Hardware
---

### Post by Amios on 2010-04-18
Hey.
I've got a new Mouse (Logitech MX1100). I've pluged it into my pc and started my os.
But the mouse is much to fast. So fast that i am not able to work with it. So i turned down the mouse speed to the lowest value. But the mouse is still to fast. How can i turn the speed down?

In Windows I've no issues with the speed.

---

### Post by khelben1979 on 2010-04-19
```
sudo apt-get install lomoco
```

```
lomoco -4
``` (speed 400 dpi)
or
```
lomoco -8
``` (speed 800 dpi)

See the man page for more options:
```
man lomoco
```

---

### Post by Amios on 2010-04-19
i got following error:

```
003.002: 046d:c526 Unsupported Logitech device: Unknown

```

my xorg.conf looks as following

```
Section "InputDevice"
Identifier      "Logitech MX1100"
Driver          "evdev"
#Option          "Name"          "PS2++ Logitech MX Mouse"
Option           "Name"         "Logitech USB Receiver"
#Option      "Phys" "*/input0"
Option      "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
#Option          "HWHEELRelativeAxisButtons" "7 6"
Option          "MinSpeed" "0.02"
Option          "MaxSpeed" "0.10"
#Option          "Resolution" "1600"
Option "Sensitivity" "1"
Option "Resolution" "10"
Option          "ZAxisMapping" "4 5"
Option          "AccelFactor" "0.020"
Option          "NoAccel"
EndSection

```

---

### Post by khelben1979 on 2010-04-19
Have you edited that xorg.conf file manually?

---

### Post by Amios on 2010-04-19
> **khelben1979 said:**
> Have you edited that xorg.conf file manually?
yes

edited /lib/udev/rules.d/40-lomoco.rules and inserted 

```

# "C-BUF34",  "Receiver for MX1100 Laser"
ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c526", RUN+="udev.lomoco"

```
still "unsupported device"

---

### Post by khelben1979 on 2010-04-19
If your Linux system cannot identify your usb Logitech mouse, then it's probably because there is no hardware support for it inside the Linux kernel you're using.

What version of Ubuntu are you running?

---

### Post by Amios on 2010-04-19
Karmic Koala

Should i maybe build a new xorg.conf?

removed the hole Section Inputdevice and rebooted. No change in "sudo lomoco -i"

---

### Post by khelben1979 on 2010-04-19
> **Amios said:**
> Should i maybe build a new xorg.conf?

Yes! Doing a backup of your present xorg.conf is a good idea though.

---

### Post by Amios on 2010-04-19
Deleted the xorg.conf, created a new one as mentioned here [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

typed in > sudo locmoco -8

response:
> 003.002: 046d:c526 Unsupported Logitech device: Unknown

No changes

---

### Post by khelben1979 on 2010-04-19
Have you tried changing the mouse speed by clicking on the DPI buttons on the mouse?

You can also read [this]("http://www.phoronix.com/scan.php?page=article&item=logitech_mx1100&num=3") from Phoronix.

---

### Post by Amios on 2010-04-19
> **khelben1979 said:**
> Have you tried changing the mouse speed by clicking on the DPI buttons on the mouse?

You can also read [this]("http://www.phoronix.com/scan.php?page=article&item=logitech_mx1100&num=3") from Phoronix.
Yes I've read it. I think its an oblivious question about clicking the dpi buttons, but shure  I have :)

The Question is, why lomoco do not work.

---

### Post by khelben1979 on 2010-04-19
It works on my Debian system and I have 2 logitech mices connected. I think the problem could be that the lomoco software is too old for your specific model of the mouse, I'm not sure. Perhaps you should e-mail the lomoco developers and ask them? :D

---

### Post by Amios on 2010-04-19
> **khelben1979 said:**
> It works on my Debian system and I have 2 logitech mices connected. I think the problem could be that the lomoco software is too old for your specific model of the mouse, I'm not sure. Perhaps you should e-mail the lomoco developers and ask them? :D

already done. Any other clue to solve my problem?

---

### Post by Amios on 2010-04-20
have written a new patch for lomoco to handle mx1100.
seems not to work :/

---

### Post by khelben1979 on 2010-04-20
> **Amios said:**
> have written a new patch for lomoco to handle mx1100.
seems not to work :/

Did you code the patch?

---

### Post by Amios on 2010-04-20
> **khelben1979 said:**
> Did you code the patch?
yes, I did. But cant write to USB-device. I contacted one of the developers and asked him to help.

---

