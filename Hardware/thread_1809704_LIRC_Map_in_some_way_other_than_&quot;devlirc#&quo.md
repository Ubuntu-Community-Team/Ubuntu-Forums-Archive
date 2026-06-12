---
title: "LIRC: Map in some way other than &quot;/dev/lirc#&quot; or event-number?"
date: 2011-07-22
forum: Hardware
---

### Post by Nicezia on 2011-07-22
I have two remote devices in my computer... one built into my TV-card and the other is a MCE Remote Receiver. I like the MCE receiver, because I'm not restricted to just one remote (cause i misplace my universal remote often, which i use as my main remote.) Well every few boots or so my devices invert (my TV-card remote device will change from lirc0/event6 to lirc1/event8, and my MCE receiver will change from lirc1/event8 to lirc0/event6 and vice versa)
this is without me moving the usb port the MCE receiver or the pci slot of the tv card (only thing that gets moved around are my mobile devices (ipod/windowsmobilephone/usb flash drives) sometimes one or another is plugged in when i boot/reboot sometimes none, I'm not sure if that would effect event and device ordering at all, all i know is my input devices aren't always mapped the same, so i lose lirc functionality at the whim of the device/event-mapping...

so i was wondering if there is a foolproof way to set in the hardware.conf the device to use (currently bouncing from /dev/input/lirc0 to dev/input/lirc1 when necessary) so that i don't have to modify it every time.


this is probably more an lirc question, but i'm asking here because if there isn't a way to do this is there at least a way to lock Ubuntu into setting lirc1 for the MCE reciever?

BTW: this is a HTPC setup otherwise  meddling with the settings everytime wouldn't bother me!

System Specs
Processor: Intel Dual Core2 Duo 2.8Ghz
Memory: 4GB Corsair
Video Card: nVidia GeForce GT 520
Sound Card: Onboard 5.1 Surround
TV Card: Pinnacle i800 Hybrid ATSC/NTSC
Periperirals: Logitech Wireless Keyboard/Mouse Combo
              External Hitachi 2TB Drive
              iPod, Windows Mobile Phones
              MCE eHome Remote Reciever

Ubuntu 11.04

Harware

---

### Post by Nicezia on 2011-07-22
please?

---

### Post by Nicezia on 2011-07-24
my last plea!

---

