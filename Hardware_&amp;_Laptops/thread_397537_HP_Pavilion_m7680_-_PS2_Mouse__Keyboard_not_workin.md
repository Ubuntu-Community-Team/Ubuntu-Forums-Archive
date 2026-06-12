---
title: "HP Pavilion m7680 - PS/2 Mouse / Keyboard not working"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by Shakarhaba on 2007-03-30
Hey, Im having a trouble with ubuntu and my mouse/keyboard.
When I connect the mouse and the HP keyboard to the PS/2 port Ubuntu doesnt recognize them when Its loaded, (The computer recognices it Windows / GRUB...)

So what should I do to make them work? Maybe install a driver or something?
By the way Im pretty new using Linux so talk to me as If I was nerdy.

Thanks! :D

---

### Post by Ireclan on 2007-03-30
What does your "Xorg.conf" file say about your mouse? The file should be located in "/etc/X11". The section you are looking for looks simular to this:

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Post this section here. We'll see if anything looks abnormal. As for your keyboard problem...I'll give it a shot after we solve this mouse problem (or fail in the attempt), but I haven't really needed to mess around with that section of xorg.conf, so I'm not sure how helpful I can be.

---

### Post by Shakarhaba on 2007-03-31
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc10"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Than'ts how they look like :)

---

### Post by Ireclan on 2007-03-31
Well, we COULD try changing the protocol of your mouse, depending on what type it is. But honestly, nothing really looks abnormal. What type of mouse do you have (ie PS/2, wireless, USB, etc...). Here's something to try: replace the text "ExplorerPS/2" with "Auto". If that doesn't work, try replacing the text with "IMPS/2". If THAT doesn't work, replace the text with the original protocol, and I'm sorry I couldn't be of more assistance.

As for your keyboard, again, nothing looks abnormal. Your model appears to be different from mine, as does your keyboard layout. Does your keyboard have a spanish layout? Because that would appear to be what xorg has it as. If you do not wish to have a Spanish keyboard layout, change the text where it says "es" under "XkbLayout" to read "us" (assuming you want a United States English keyboard layout instead). We could also try changing your keyboard model, but that may render your keyboard nonfunctional (I've never needed to do this, so I'm merely assuming that it might). If you're feeling brave, go ahead and change the text reading "pc10" under "XkbModel" to read "pc105" (which is mine, and I have a functioning keyboard). If this doesn't help, then again, I'm sorry I couldn't be of more assistance, and do remember to replace your modifications back the way they were before.

---

