---
title: "disabling left and right mouse scrolling?"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by dyzzy on 2007-01-02
I've seen some threads asking how to set up extra mouse buttons but I want to know how to disable my mouse's left and right scrolling (when you click the mouse wheel left or right it scrolls that way). Ubuntu set it up automatically and it's really annoying for me. Here is the mouse section of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by tweedledee on 2007-01-06
> **dyzzy said:**
> I've seen some threads asking how to set up extra mouse buttons but I want to know how to disable my mouse's left and right scrolling (when you click the mouse wheel left or right it scrolls that way). Ubuntu set it up automatically and it's really annoying for me. Here is the mouse section of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Run "xev" in a terminal to see what button event is being triggered when you press the wheel left or right, then use xmodmap to remap those two buttons to 2 inactive positions.

---

