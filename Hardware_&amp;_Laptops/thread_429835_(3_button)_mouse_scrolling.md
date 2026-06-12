---
title: "(3 button) mouse scrolling"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by E87 on 2007-05-01
Hi guys im a bit new to ubuntu and the only problem i have is icant use the mouse scrolling...

this is my info:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true" and im using Feisty with a ROCKETFISH  BLUETOOTH OPTICAL MOUSE&KEYBOARD
any help would be great thanks guys

---

### Post by dcstar on 2007-05-02
> **E87 said:**
> Hi guys im a bit new to ubuntu and the only problem i have is icant use the mouse scrolling...

this is my info:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true" and im using Feisty with a ROCKETFISH  BLUETOOTH OPTICAL MOUSE&KEYBOARD
any help would be great thanks guys

Assuming you actually have a 3-button mouse, then you may not need to "Emulate", so set that option to "False" and restart.

---

