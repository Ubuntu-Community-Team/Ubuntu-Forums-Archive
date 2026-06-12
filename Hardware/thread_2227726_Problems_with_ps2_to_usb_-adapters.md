---
title: "Problems with ps/2 to usb -adapters"
date: 2014-06-03
forum: Hardware
---

### Post by Rooster2000 on 2014-06-03
I bought from eBay two of these ps/2 to usb -adapters which I hoped to connect my ps/2 mouse and keyboard to my laptop that doesn't have any ps/2 ports. Unfortunately it seems that these adapters don't work the way I expected. I have tested them now with three different computers, two different mouses and keyboards without any success. The other mouse - which has led inside - does light up, and the other keyboard blinks it's lights about once every 30s when they are connected, so there seems to be some kind of connection.

For two computers, Abit KT7 and Asus A6000, that have Lubuntu 14.04 LTS installed, neither dmesg or lsusb show a reaction when I plug ps/2 mouse via adapter to any of the usb ports. Instead, my third computer, HP Pavillion t849 that has Xubuntu 12.04 LTS, does write these lines in the end of dmesg

```
[  305.948056] hub 2-0:1.0: unable to enumerate USB device on port 3
[  310.752049] hub 2-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
```

This is also the only computer that has USB Legacy -option available - and thus enabled - in BIOS.

Has anyone got similar adapters working? Are there some requirements for motherboards, usb-ports or ps/2 keyboards or mouses in order to use these adapters? Or are these adapters some wrong type? Unfortunately I don't have usb keyboard/mouse to test, but all the usb ports in these computers recognize other usb deivces, like memory sticks.

---

### Post by TheFu on 2014-06-03
I've been using the 'y' connectors for years without issues. Have 6 of them here from 2 different makers.  Think they were $6 each from Amazon. Something like this [http://www.amazon.com/SANOXY®-USB-PS-2-Adapter/dp/B00007AP2O](http://www.amazon.com/SANOXY®-USB-PS-2-Adapter/dp/B00007AP2O)  - look cheaper now.  In the old days, enabling Legacy USB support in the BIOS was needed.  Haven't needed that for awhile that I recall - of course those old systems still have it enabled.

---

### Post by sudodus on 2014-06-03
I have a Belkin USB dual PS/2 adapter which can connect a mouse and a keyboard via a single USB port to a computer. It works for me.

[http://www.belkin.com/us/F5U119E/p/P-F5U119E/](http://www.belkin.com/us/F5U119E/p/P-F5U119E/)

---

### Post by Rooster2000 on 2014-06-04
Hmm, ok. Perhaps I am going to test one of those dual adapters too. Got to try to borrow USB mouse or keyboard somewhere for testing too.

---

### Post by Rooster2000 on 2014-06-19
I bought one of those dual 'y' -adapters and it started to work out just fine for both mouse and keyboard. I suppose those earlier adapters were just bad ones or something.

---

### Post by saurkulsh2 on 2014-09-07
I only wanted to use the keyboard using the Y-connector and had a really old ps2 keyboard and connector lying around...
This technique apparently worked for me:
1. Connect the keyboard to the mouse ps/2 in the y connector and connect the y cable to a usb port.
2. Remove and now connect the keyboard's I/O to into its right connector on the Y connector.
3. Press the num key on the keyboard, then use the numpad and then all the keys should start working!
Do this every time the system doesn't detect the keyboard.
This could get you through a day or so until you wait for a new USB keyboard to be shipped to you :P

---

