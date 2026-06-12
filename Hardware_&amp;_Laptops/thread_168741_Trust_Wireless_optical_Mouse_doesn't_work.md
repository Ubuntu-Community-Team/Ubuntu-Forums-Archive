---
title: "Trust Wireless optical Mouse doesn't work"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by lrnzcpmn on 2006-05-01
It seems I made a bad choise with buying a 'Trust Wireless Optical Mouse' model MI-4100 (usb). It doesn't function. Does anybody have a suggestion or a working Trust mouse? Or should I just return it to the shop ? 
OS Ubuntu Breezy & Dapper i386.

---

### Post by lrnzcpmn on 2006-05-01
Resolved, It was a not connected usb port on my pc. Stupid I know.:???:

---

### Post by Zimmer on 2006-05-01
Ensure you left click to wake it up (after first using the button on the base to link it to the base station). They tend to go to sleep if left alone, like a screensaver...
What are your xorg.conf settings like?
a simple :
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
works for my cheapo wireless set..

EDIT: you posted while I was typing!!

---

