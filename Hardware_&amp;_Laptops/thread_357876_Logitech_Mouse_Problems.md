---
title: "Logitech Mouse Problems"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Mencius on 2007-02-10
I have a Logitech MX518 Optical mouse, When Ubuntu starts up it works perfectly for between 5 and 10 minutes but then it just stops working, the optical light stays on but the cursor doesn't move.

It normally happens when I click the software update button, or when I launch or close Firefox.

I am using V 6.10.

---

### Post by noknyc on 2007-02-10
I'm having the same problem... very frustrating.  I can get it working again if I unplug the usb and then plug it back in.  But that gets annoying every few minutes.

Using Edgy.  The mouse is a Logitech MX300.  Everything else (including other USB devices) are working just fine.

I've fiddled a TINY bit with my xorg.conf... but I was afraid I'd make matter worse.  Here is the applicable section:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"
EndSection

Any ideas?  What other info would be helpful?  Thanks!

---

### Post by Daveth on 2007-02-11
Yes, my MX310 does the same thing. A slight improvment occurs if you try different usb ports. Touch wood, mine freezes less now I moved it to one of the rear ports as opposed to one of the ones at the front, which are on motherboard headers. Annoyingly, when I first started up Ubuntu it never froze at all. I'm currently blaming a  java install- not that that gets me anywhere!

---

### Post by komitski on 2007-02-11
You have to exchange the mouse battery first.
This is the first action you can perform.
This is my opinion, any way.

---

### Post by noknyc on 2007-02-11
My mouse is not wireless... no battery to remove.  

I've also tried several different USB ports with no apparent difference.

---

### Post by menkent on 2007-02-12
seems like an ongoing problem (somehow related to power management?)

[http://www.ubuntuforums.org/showthread.php?t=28173](http://www.ubuntuforums.org/showthread.php?t=28173)

---

