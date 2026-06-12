---
title: "[SOLVED] G.E. optical mouse- cofiguring buttons in xorg.conf"
date: 2008-09-17
forum: Hardware
---

### Post by fewjr on 2008-09-17
Hello All,
I have a question about my xorg.config > inputdevice section. This is all that is in my file:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

I do not see the options for number of buttons.My mouse is a generic mouse with a left & right buttons, a scroll wheel which can be clicked down. The only thing that is not working is the clicking of the wheel. I can scroll with the wheel but can not click the wheel to for example, bring up the little 4-way arrow in a webpage which allows me to scroll by moving the mouse up & down. According to the "ManyButtonsMouseHowto" this type of mouse is considered a 5 button mouse and should be working by default in a Gnome environment. Just wondering why I have no button options and what I should change in the file.
Thanks
fewjr

---

### Post by pbpersson on 2008-09-19
I **totally** reconfigured my xorg.conf because I was very unhappy with how my mouse worked.  Here is how it looks on all my Ubuntu systems, it is a two-button mouse with a wheel:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"XAxisMapping"	"6 7"
	Option		"ButtonMapping"	"1 2 3 4 5"
	Option		"Buttons" "5"
	Option		"Emulate3Buttons"  "false"
EndSection
```

I don't know if this will give you the functions you want, but you will have some buttons to play with in your config file.  Be sure you save your old file in case my advice totally messes up your world.

---

### Post by cb951303 on 2008-09-19
AFAIK the 4 way arrow is a Windows thing (IE's feature I think)
Try selecting a text and pasting it with middle click. You'll see if it works or not

---

### Post by fewjr on 2008-09-19
Well there you have. I never thought about it being a windows thing. I knew it was something simple. The click wheel does paste. So I guess thats what it is supposed to do in Linux. Thank you very much pbpersson and cb951303.

---

