---
title: "[SOLVED] Wheel Mouse Problem"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by Norwal on 2006-01-08
Hello,

I seem to be having a wheel mouse problem.  The wheel scrolls down the page fine but if I try to wheel back up the page the wheel acts as if I did a right click. I have a Logitec Cordless Optical Mouse.

xorg.conf look like this

ection "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

The interesting thing is that it happened in SUSE 10 but was fixed in SUSE after a complete reinstal. (That was a partition nightmare. Hey but I learned something out of it.)

Thx

Nor

---

### Post by Norwal on 2006-01-08
WOW tuff crowd.  Not one reply.

So what's the trick to get a look?

---

### Post by Norwal on 2006-01-08
For those with the same problem I found the answer.

I have a Logitech keyboard and mouse.

follow this link

[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

---

