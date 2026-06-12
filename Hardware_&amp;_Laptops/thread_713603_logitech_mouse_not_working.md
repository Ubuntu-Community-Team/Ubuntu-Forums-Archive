---
title: "logitech mouse not working"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by meatwad64 on 2008-03-02
I have a logitech v320 mouse for my laptop and it doesn't seem to work at all. I plug it in and the mouse cursor doesn't move at all. Is there anything that needs done to get this to work? Has anyone else used this mouse with ubuntu? I'm running hardy also.

---

### Post by steveneddy on 2008-03-02
It's not a Bluetooth mouse.

All of my non-bluetooth mice hook as soon as I plug the USB dongle in.

Someone will ask you a few technical questions now.

Um, simple question. Do you have good batteries in the mouse?

---

### Post by meatwad64 on 2008-03-02
Yeah that was what I was afraid of so I booted into windows and it worked just fine. I was searching on google and found a special xorg.conf configuration for a v320 and I wonder if this means its a special case. 

This is what it looked like:

Logitech V320 Wireless
File: /etc/X11/xorg.conf

Section "InputDevice"
	Identifier "Mouse2"
	Driver "evdev"
	Option "Name" "Logitech USB Receiver"
        Option "HWHEELRelativeAxisButtons" "7 6"
EndSection



I haven't tried it yet but i see it uses the evdev driver. So i'm not sure if this mouse has to use a special driver or not. I've never had a usb mouse that required any special configuration.

---

