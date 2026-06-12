---
title: "Drivers for Eagle Touch Ergonomic Keyboard"
date: 2011-12-27
forum: Hardware
---

### Post by minhuang on 2011-12-27
Hello.  I have an Eagle Touch Ergonomic Keyboard; here are the relevant specs:

Product Information
Manufacturer: ADESSO
Product Line: Eagle Touch
Device Type: Ergonomic
Interface: AT or Serial
Color: White

This keyboard has an integrated trackpoint/nipple mouse in the middle (here's a picture: [http://www.ebay.com/itm/New-Ergonomic-Comfort-Keyboard-ADESSO-Model-Eagle-Touch-/120831734919?pt=PCA_Mice_Trackballs&hash=item1c2221f487#ht_1633wt_1016](http://www.ebay.com/itm/New-Ergonomic-Comfort-Keyboard-ADESSO-Model-Eagle-Touch-/120831734919?pt=PCA_Mice_Trackballs&hash=item1c2221f487#ht_1633wt_1016)).

I'm connecting it to my machine with a serial to ps2 cable, which allows the keyboard itself to function, but the nipple mouse does not.  Does anybody have any ideas about how to get the mouse to work?

Thanks

---

### Post by wolfen69 on 2011-12-27
Try
```
sudo apt-get install gpointing-device-settings tpconfig
```
and reboot. Tpconfig is for modifying the configuration.

---

### Post by minhuang on 2011-12-27
I tried that out; tpconfig suggests that there is a mouse there

```

[minhuang@warking:~]$ sudo tpconfig -i
[sudo] password for minhuang: 
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

...but gpointing-device-settings shows only my usb mouse.  Rebooting does not solve anything :(

---

