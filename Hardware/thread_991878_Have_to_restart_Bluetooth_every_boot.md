---
title: "Have to restart Bluetooth every boot"
date: 2008-11-24
forum: Hardware
---

### Post by yeehi on 2008-11-24
ALogitech Cordless Desktop® MX™ 5000 Laser mouse/keyboard is connected to Intrepid Ibex AMD 64 alternate.

After every boot there is no longer a bluetooth connection to the mouse and keyboard and a wired connection is necessary.

How is it possible to set up the system so that it remembers the paired devices?

Is there a linux version of the logitech software available anywhere?

Thank you!

:)

---

### Post by Yezinki on 2008-11-24
Hi there,

What BT device are you using...BT dongle or a BT module?

Regards,

Yezinki.

---

### Post by slothbotkiller on 2008-11-25
> **yeehi said:**
> ALogitech Cordless Desktop® MX™ 5000 Laser mouse/keyboard is connected to Intrepid Ibex AMD 64 alternate.

After every boot there is no longer a bluetooth connection to the mouse and keyboard and a wired connection is necessary.

How is it possible to set up the system so that it remembers the paired devices?

Is there a linux version of the logitech software available anywhere?

Thank you!

:)

Okay, this one is easy -- that is it is easy if you are having trouble with your bluetooth mouse connection on Ubuntu Intrepid Ibex (I suppose it would be the same for some of the older versions): navigate to the bluetooth applet up in the right hand corner of the screen right-click, navigate to Preferences, left-click and search for the visibility setting "Always Visible," click and enjoy. If you want you can restart to check if it works. 

Cheers, Brian.

---

### Post by yeehi on 2008-11-26
It is the Logitech wireless mouse/keyboard bluetooth. I tried the ¨always visible¨ setting and will wait to see how things go after reboot.

---

### Post by HyRax on 2008-12-26
The current Intrepid issue with Bluetooth appears to be that it doesn't scan for devices to reconnect. Currently I am using [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6) with my Bluetooth mouse with great success so far.

---

