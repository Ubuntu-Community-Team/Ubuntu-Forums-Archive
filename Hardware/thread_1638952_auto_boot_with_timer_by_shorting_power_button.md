---
title: "auto boot with timer by shorting power button"
date: 2010-12-06
forum: Hardware
---

### Post by meg23 on 2010-12-06
I have a relatively basic hardware question for auto booting a desktop computer. I know that is possible to start up my pc by shorting the powerbutton by contacting 2 wires connected to the proper pins. What I would like to do is attach these wires to some sort of timer and have them contact for a split second to auto boot the machine at a specified time. Is there any available timer that would allow me to achieve this, with mods or without mods?

---

### Post by pricetech on 2010-12-06
Probably.  I check with your local electronics hobby store or electronics supplier.

Better option is to set Auto On in your BIOS, if available.

If on a network with other computers that stay on all the time, Wake on LAN is also an option.

---

### Post by meg23 on 2010-12-06
Well, I don't know of any local electronics store except for Radioshack and they usually don't know much about electronics except for hdmi cables. I also don't have an "electronics supplier." I guess the real question is, what do you call a timer that completes a circuit when activated? Is is a relay timer?

---

### Post by pricetech on 2010-12-07
Sounds like one of my projects from some years ago.

Just explain to your supplier, whomever that may be, that you want a timer that will close a circuit momentarily at a set time.  They should be able to help you with something.  I think the circuit itself is called a "one shot" or something similar, but don't quote me since there are a lot of cobwebs in that part of my brain.

Does your BIOS not support turning the system on at a certain time ??

If not, does it support turning on after a power failure ??  If that's supported then you could put it on a timer used for lights and such that simply turns on at a certain time and off at a certain time.  You'd want to write something in the OS to shut down before the timer turns off though, unless you'll be there to shut it down manually.

---

### Post by meg23 on 2010-12-07
The bios does not support timed booting. I tried the power failure settings however it did not seem to work. 

It seems like a pretty simple project, I just can't figure out what kind of timer I need.

---

### Post by pricetech on 2010-12-07
You may have to build it yourself.

If I were "frankensteining" this, I'd start with a cheap plug in timer.  I'd plug in a power supply that would power a relay which, when energized, would close the circuit for the power switch.

Biggest problem with that is the wall timer having a short enough duration to turn back off quickly.

I'm sure there's a better solution if you know what sort of logic circuits to put together.

---

