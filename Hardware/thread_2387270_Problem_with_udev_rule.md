---
title: "Problem with udev rule"
date: 2018-03-16
forum: Hardware
---

### Post by wrybread on 2018-03-16
I'm trying to assign a specific /dev/input address to a specific joystick using udev, and having trouble.

Following this guide:

[https://ubuntuforums.org/showthread.php?t=1595666](https://ubuntuforums.org/showthread.php?t=1595666)

I made a file named /etc/udev/rules.d/73-persistent-joystick.rules, set it to chmod 755, with the contents:

KERNEL=="js?", ENV{ID_VENDOR}=="Saitek", ENV{ID_MODEL}=="Saitek_P2900_Wireless_Pad", NAME="input/js4"

That *should* make that joystick be /dev/input/js4, right? The ID_VENDOR and ID_MODEL are confirmed correct.

Is there anything else I need to do to make it use the address js4? Or any other method?

Currently it seems that my udev rule isn't having any effect at all.

I'm trying to make sure that joystick is always last. My other two joysticks have identical ID_VENDOR and ID_MODEL strings. Their udev lines would look like:

KERNEL=="js?", ENV{ID_VENDOR}=="DragonRise_Inc.", ENV{ID_MODEL}=="Generic_USB_Joystick", NAME="input/js0"
KERNEL=="js?", ENV{ID_VENDOR}=="DragonRise_Inc.", ENV{ID_MODEL}=="Generic_USB_Joystick", NAME="input/js1"
KERNEL=="js?", ENV{ID_VENDOR}=="Saitek", ENV{ID_MODEL}=="Saitek_P2900_Wireless_Pad", NAME="input/js2"

But that doesn't seem to have any effect either.

Any ideas?

---

