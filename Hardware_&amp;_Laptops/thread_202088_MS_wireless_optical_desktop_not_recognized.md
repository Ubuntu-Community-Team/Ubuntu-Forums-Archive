---
title: "MS wireless optical desktop not recognized"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by lewisdw on 2006-06-22
I'm running ubuntu dapper 6.06 on an amd 64 in a gigabyte s series motherboard with 1gb of RAM.  I booting from the live DVD and have connected my microsoft wireless optical desktop receiver (single receiver for the keyboard and mouse) via USB (have tested on a winxp system with no problems), and ubuntu does not respond to the keyboard or mouse.  If I reboot with the receiver plugged into the ps2 port, the keyboard works but not the mouse.  I've looked in my bios for a "legacy usb" support option, but do not see one.

Any help is appreciated in getting this working.

---

### Post by will_in_wi on 2006-06-22
There might be bios settings to help. Can you access the bios with the usb mouse and keyboard?

---

### Post by lewisdw on 2006-06-22
Yes, the keyboard works at POST and in the bios menus.  I also seem to have keyboard functionality in grub.  However, I can't tell you for sure that the mouse is seen at that time.

---

### Post by monomaniacpat on 2006-06-30
Well it worked for me off the Live CD. Are you sure you've used the hardware to connect the decives over the wireless? I.e. pressed the buttons on both the transmitter and mouse. I have to do this every time I change from one computer to another.

---

### Post by zapho on 2006-08-24
Sorry for reopening a old thread, but I've also got a microsoft wireless desktop that I can't get working. (Everything I've managed to get working.) I found that if you go to device manager under the usb section, the device keeps connecting and then disconnecting, continuously. This happens about once a second. When connected, you hit the "connection" button the receiver, but of course it doesn't get enough time to work before disconnecting. Anyone have any ideas?

I also have another, seperate microsoft wireles mouse, which works just fine. I'm running this off a laptop so the PS/2 option is out.

---

### Post by derekwied on 2006-09-09
I have this exact same problem and i cannot find a solution anywhere. this is really annoying. the transceiver light just blinks really fast like its only half-connected and it does this when the hardware drivers get loaded at start up is when it begins

---

### Post by zart on 2006-12-21
I've got the same thing happening and haven't been able to find any help for this issue.](*,) 

I've got the Microsoft Wireless Comfort Keyboard 1.0A, and it works fine during POST, GRUB, and when I boot into XP, but as soon as Ubuntu starts loading it's drivers I lose the keyboard.

-I've set the USB keyboard in the BIOS to enabled...
-I went into System->Preferences->Keyboard->Layouts and set the layout model to microsoft wireless multimedia


When I look in Device Manager I also see something appearing and disappearing in the USB manager, but I can't see what it is.

HELP!

---

### Post by zart on 2007-01-24
I'm really disappointed in these forums.  I'd heard that Linux had this great helpful community, but there are a ton of people, apparently, with the same problem, but no helpful suggestions.

Really really disappointed.

---

