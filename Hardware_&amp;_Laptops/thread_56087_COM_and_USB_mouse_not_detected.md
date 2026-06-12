---
title: "COM and USB mouse not detected"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by agro1986 on 2005-08-11
I installed Hoary on my father's machine:



PC-Chips mobo (dunno the chipset)

Pentium II 350 MHz

256MB SDRAM

SiS 620 VGA (onboard, uses 8MB of system RAM)

PCI USB card (2 USB ports)



There's no PS/2 mouse port, so I can only use a COM or USB mouse. Curiously there's an option "Enable PS/2 mouse support" in the BIOS.



After Hoary is installed, everthing seems to work except for the mouse (including internet, I'm browsing using mouseless ubuntu now!). Tried the COM mouse (which previously worked under XP), didn't work (tried setting the PS/2 mouse stuff in the BIOS to "enable" and then "disable"). Tried a USB mouse (which worked on another XP machine), didn't work. I think the problem is not with the USB card since my USB flash disk worked flawlessly in Hoary.



There must be some workaround to this problem. Would someone care to walktrough me?  Is it possible to "force" Hoary to read any input from the COM1 port and interpret it as a mouse input? Btw, my COM mouse is a 3 button mouse  with no scroll button (so the middle/3rd button is just a plain button).



Thanks a lot,



Agro

---

### Post by heimo on 2005-08-11
Have you seen this?
[https://wiki.ubuntu.com/SerialMouseHowto]("https://wiki.ubuntu.com/SerialMouseHowto")



BTW, Welcome on Ubuntuforums, we'll be glad to help you.

---

### Post by agro1986 on 2005-08-13
Thanks for the link. After following the link, the mouse is usable BUT before the mouse could work I need to wiggle it for some seconds (as in waking the mouse up). Need to do that everytime I boot. Kinda annoying, but atleast it works.

Once again, thanks!

---

### Post by PeP on 2005-08-13
it 's starnge that xorg doesn't  reconises our usb mouse

do you have a mouse section like this?
```

Section "InputDevice"
	Identifier  "USB Mouse"
	Driver	  "mouse"
	Option	  "Protocol"	  "IMPS/2"
	Option	  "Device"		"/dev/psaux"

	Option	  "ZAxisMapping"   "4 5"
	Option	  "Buttons"	   "5"

EndSection

```

and then in 
Section "ServerLayout"
```

 InputDevice "USB Mouse" "CorePointer"

```

---

