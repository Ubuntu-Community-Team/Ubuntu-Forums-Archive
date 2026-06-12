---
title: "Macally iWebKey"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by Demogorge on 2006-12-26
Hey all,

I cannot get this USB keyboard+mouse to work in X. The keyboard works fine, but the mouse doesn't work.

If I set the protocol to auto in xorg.conf, I cannot even use my regular mouse (logitech mx500 hooked up ps/2, currently using the explorerps/2 protocol). I get about 10 "Macally Mouse: Guessing protocol PS/2" type messages in my Xorg.log, and if I try to move my regular mouse, X just restarts.

If I set the protocol to "explorerps/2" or "imps/2" my ps/2 mouse works fine, but the iwebkey mouse jumps around the screen. It jumps to the corners and clicks (i used to see behavior like this in dos when the wrong mouse driver was installed). 

The first thing I would like to try is other protocols. I have tried "evdev", but I get:

(**) Option "Protocol" "evdev"
(EE) Macally Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Macally Mouse"
(II) UnloadModule: "mouse"

Same for "vuid" and "usb". The mouse works in Windows with no special drivers installed, so I assume it can be used as a generic device in Ubuntu as well.

Sorry for the ramble... my first question is: Can I add more mouse protocols to X? Is there a list of protocols that I could try? Is that the right direction for me to go here :-? 

Thanks 8)

---

### Post by Demogorge on 2007-03-18
I finally got this mouse to work by just using the evdev protocol and creating a udev rule to map the device to a /dev/input/event* link. Apparently the evdev protocol requires that the device be of the "/dev/input/event*" form. I had to use the modalias for mapping since there was nothing else unique about the device.

---

### Post by rabidsnail on 2007-11-24
Can you post the appropriate parts of your xorg.conf?

---

