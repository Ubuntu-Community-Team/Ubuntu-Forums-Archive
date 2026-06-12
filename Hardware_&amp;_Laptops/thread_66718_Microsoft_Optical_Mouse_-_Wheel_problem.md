---
title: "Microsoft Optical Mouse - Wheel problem"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by Fottemberg on 2005-09-18
Hi guys! :)
I have a problem. After Ubuntu installation the mouse is perfectly recognized, except for the wheel. I can, with it, copy and paste, but I can't scroll the pages. What can I do?

This is the part of xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Thank you. ;)

---

### Post by docmanny on 2005-09-18
Add this to the section.

 Option "ZAxisMapping"  "4 5"

---

### Post by Fottemberg on 2005-09-18
[QUOTE=docmanny]Add this to the section.

 Option "ZAxisMapping"  "4 5"[/QUOTE]
Now it works. Thank you a lot.  :smile:

---

### Post by StorM_GmA on 2008-03-12
hi! It's a bit old topic but I also have a problem with the mouse wheel... I can scroll the pages but if I click the wheel, it does nothing. It should let me scroll just by moving the mouse but it doesn't. The line docmanny mentioned is already in my xorg.conf ...
what should I do?

---

