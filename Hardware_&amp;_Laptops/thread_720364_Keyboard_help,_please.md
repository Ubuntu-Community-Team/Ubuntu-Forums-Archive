---
title: "Keyboard help, please?"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by sammi.jo on 2008-03-10
Let me start by telling you that I'm an absolute noob. But hi!

Here's my problem: When I set my keyboard settings to UK English, it still doesn't work<properly. I have @ instead of " on 2, # instead of pound sign on 3, > instead of |, and | instead of a tilde!

I've gone into xorg.conf, and set it to 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en"
EndSection

but it still doesn't stay put! At first it worked, but now it's just swapped back! I have 7.10 Gutsy Gibbon.

Also, it doesn't always go to (what I assume to be a US keyboard). Once, it went to Turkish, but still said UK in system>preferences>keyboard.

Any help greatly appreciated! x


Oh, I think I've fixed it; I set the XkbLayout to GB to see if it did anything, and it seems to work!

---

### Post by rossjman1 on 2008-03-10
Try setting your keyboard layout as pc104 which should be the default. I noticed that you have pc105 ( I couldn't tell if this was accidental or not ).

---

### Post by sammi.jo on 2008-03-10
Ah, thanks. I was wondering what the default was!

---

