---
title: "Acer Aspire 5741 backlight doesn't work 10.10"
date: 2010-10-02
forum: Hardware
---

### Post by niko123456 on 2010-10-02
hi all,

I just installed the 10.10 release candidate.

during installation I noticed the backlight had been switched off. i was able to fix this by closing and opening the lid, with the backlight switching back on.

once ubuntu had been properly installed however, the backlight still fails to work, and closing the lid makes the computer suspend (that bit works!!). so I am unable to even trick the computer into switching the backlight back on. 

does anyone know a workaround so I can at least tell ubuntu to turn off suspend when I shut the lid? or better yet, a fix?

I had a look in the bugtracker and there is something similar, but its for ATI (I have Intel video drivers), and my backlight fails on boot.

---

### Post by niko123456 on 2010-10-02
Another thought..

Does anyone know how to file a bug report online without being inside ubuntu? its a bit hard to file a bug when I can't see the screen.

---

### Post by Frostshock on 2010-10-03
You actually had it working in 10.4? I had to modify a GRUB file to get backlight control or it would be stuck on max brightness, and even then the backlight resets when the display goes to sleep.

Laptop backlighting is just a very touchy subject altogether it seems.

---

### Post by niko123456 on 2010-10-03
It was useable.

The annoying thing about this instance was that I couldn't see the screen.

I found a workaround to at least get using.

Switch to another console, (ie, ctrl alt 1), then open and shut the lid (suspend is inhibited). switch back to ctrl alt 7 and then switch off automatic suspend and resume.

...now.. ideas on where to start bug reporting?

---

### Post by niko123456 on 2010-11-24
Does anyone know a helpful way of getting a bug looked at? My bug has been sitting there for ages without any action. Its really frustrating. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/653985)

---

