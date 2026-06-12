---
title: "Scroll wheel sometimes triggers RMB"
date: 2008-05-19
forum: Hardware
---

### Post by j.daniel on 2008-05-19
**Hello,**

  Just wondering if any of you know whats going on here.

  I have a Ubuntu / Gnome installation upgraded to Hardy on a regular desktop. To this I have a Logitech wireless keyboard / mouse combo (EX110 - no blue tooth, regular wireless) connected via a DLink DKVM-4K KVM switch to the PS/2 port.

  When I use the mouse scroll wheel, quite often the context menu appears - i.e. somehow a right mouse button event is triggered. It is not unusual either for a second RMB event to get triggered before I have time to react and then I have selected something from the context menu... irritating.

  Playing around here I see that it seems to be when I scroll upwards, in the end of the scroll (or if I scroll slowly upwards) there is a high probability that I end up with a context menu open.

  Anyway, looking at the man pages for xorg.conf and "man mouse" (quite funny by the way...) I see that there are different protocols for Microsoft and Logitech mice, so I am starting to wonder if the KVM switch makes Hardy believe that it it a Microsoft compatible mouse in the other end or something... just my guess.

  The relevant part of my xorg.conf is:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

In the other ports of the KVM switch I have a few variants of Windows (2K / Vista) running, and they have no such problems. 

...anyone have any ideas?

Cheers
/ Daniel

---

### Post by j.daniel on 2008-05-30
Interesting development:

Today, I noticed that I have no scroll wheel problems at all... Thinking back at what I did different today, I realize that I let the Ubuntu system boot & start with the KVM set to the Ubuntu system during the complete process.

Apparently there is some mismatch when the KVM switch is not set to the Ubuntu system at boot & startup time - the handshaking with the mouse must somehow be different.

It is still interesting that my Windows boxes exhibit no such problems.

Anyone have any ideas?

Cheers
/ Daniel

---

