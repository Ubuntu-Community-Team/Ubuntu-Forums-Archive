---
title: "Logitech MX510, btnx: Unwanted doublemapping of some buttons"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by hsiyao on 2007-12-10
Hi,

I managed to get btnx to work and compared with other solutions it's rather easy to use... with the xorg.conf part copied underneath I now have the following problem: I not only get the actual action I configured with btnx but also still got some, I guess, standard X-Actions like scroll up, scroll down, autoscroll on buttons, where I don't want it. When I change the line ZAxis-Mapping to something else, I get rid of the scrolling on the buttons but also on the wheel itsself. 
I configured my button above the wheel for example with "toggle maximisation"... when I click on a window with this button I see that besides maximization of the window, it's content is scrolled one line up.

Can anyone tell me how to get rid of this standard X actions on my configured buttons? 
Thanks in advance!!!

Jens.

here is the part of interest from my xorg.conf:
-------------
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"no"
	Option          "Buttons"               "10"
EndSection
----------------

---

### Post by daou on 2007-12-12
You can try keeping the change with your ZAxisMapping, then tell btnx to make a wheel scroll event. Bind these keycodes to your mouse wheel scrolls (you must detect the scrolls with btnx-config first): REL_WHEELFORWARD, REL_WHEELBACK

---

