---
title: "Mouse Oddities"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by brainsick on 2005-04-18
Hello,

I have a Microsoft Wireless IntelliMouse Explorer 2.0 that I am trying to get working with Ubuntu 5.04.  The mouse is a USB mouse, but I'm using the supplied USB -> PS/2 adapter so I cook hook it up to a (TRENDnet) KVM that has PS/2 ports.  The KVM mouse port is then hooked up to the computer by a PS/2 cable which connects to a (TRENDnet) USB to PS/2 Converter.  I don't connect it directly to the motherboard's PS/2 port because I have a Asus K7V8X-X which fails to initialize them properly 19 out of 20 times.

Mouse (USB) -> USB to PS/2 Adapter -> (PS/2) TRENDnet KVM -> PS/2 Cable -> TRENDnet USB to PS/2 Converter -> (USB) Computer

Without having changed the xorg.conf, the setup, surprisingly, mostly works.  It seems random as to whether or not the scroll wheel works or not.  More annoyingly, just by moving the mouse around on the screen, it seems to randomly register mouse clicks.

I understand that the above is a pretty convoluted way to hook up a mouse, but does anyone have any ideas on how to get the mouse wheel to work 100% of the time, and how to solve the random mouse clicks?

---

### Post by diebels on 2005-04-18
Don't follow the setup. You don't have a free usb port for your mouse?
Do you have
Option          "ZAxisMapping"          "4 5"
in xorg.conf?

---

### Post by brainsick on 2005-04-18
[QUOTE=diebels]Don't follow the setup. You don't have a free usb port for your mouse?
Do you have
Option          "ZAxisMapping"          "4 5"
in xorg.conf?[/QUOTE]

Yes, I have a free usb port, but the KVM doesn't support a USB mouse and I need to be able to switch the keyboard, monitor, and mouse between computers.

To further complicate things, the built-in PS/2 ports on my Asus K7V8X-X motherboard are crap, so I have to use a USB device that provides a keyboard and mouse PS/2 port.

Yes, ZAxisMapping is set in the xorg.conf.  As I said, it works sometimes and not others.

---

