---
title: "Help - HP Wireless Keyboard kills GNOME?"
date: 2009-05-31
forum: Hardware
---

### Post by francescogro on 2009-05-31
Hi all,
I'm asking for help for a most ridicolous problem.
I have an Asus A6JM laptop with kubuntu jaunty  + "ubuntu-desktop" metapackage installed. It all went more or less well, till **I plugged in the bluetooth receiver** of an HP wireless keyboard. This keyboard is part of a wireless kit composed of mouse + keyb + usb-receiver. I wanted to use the keyboard as an alternative to that of the laptop itself.
Well, the keyboard worked out of the box, but from then on my keyboard layout was changed! For example, if I tap on the wireless keyboard, all goes well, but if I use the laptop keyb, some keys are wrongly interpreted.

In particular, the (usually) FN-activated numpad (which correspond to the UIOP-JKL-M keys) seems to override the letter keys, so that I can't write properly on the laptop keyb! And this happens **regardless of the presence in the usb port of the receiver (even at boot)**   =_=

Now, the lsusb command gives (if the receiver is plugged in):
```
Bus 002 Device 002: ID 03f0:0f0c Hewlett-Packard 
```

Curious is the fact that the** gdm/kdm and KDE itself are not affected** by this distortion of the keyb layout, but only once I enter GNOME the layout gets messed.
I tried acting on the PREFs/keyboard options, but it didn't work..

I really dont know what to do.. :(
What can I do for
- disconnect completely and remove the traces of the usb-receiver
- reinstall the keyboard layout (having previously unplugged the receiver)?

I'd like not to format & reinstall.. but for now I can't use my laptop without the wireless keyboard!!

---

