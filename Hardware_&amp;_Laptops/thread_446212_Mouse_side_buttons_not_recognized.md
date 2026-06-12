---
title: "Mouse side buttons not recognized"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by HumbleGod on 2007-05-16
I just did a reinstall of Feisty, and now I'm trying to configure my Microsoft Intellimouse, which has the standard two mouse buttons and wheel, plus two buttons on the side (generally used for forward and back in the browser). However, my mouse only recognizes the first five button functions - 1 (left mouse), 2 (clicking the scroll wheel), 3 (right click), 4 and 5 (up and down on the scroll wheel). 

When I run [FONT="Courier New"]xev[/FONT], anytime I click on the side mouse buttons it only recognizes them as buttons 2 and 3, just like when middle- or right-clicking. I can't assign forward or back to my button "6" if it only recognizes it as another button 3!

Here is my xorg.conf file:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"IMPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection

```

I've tried following parts of [this guide]("http://ubuntuforums.org/showthread.php?t=316441"), but it hasn't changed anything. Does anyone have any advice?

---

### Post by treaz on 2007-05-19
I have encountered the same problem...
I have read some posts and it seems that some people care success with the following xorg.conf modd
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

However the fwd/back buttons do not work as they are supposed to, but as a horizontal wheel, try it, you'll see what i mean. If you do manage to make the buttons work properly please tell me what settings u've done.
Good luck!

L.E.: I have mistaken, the above issue appears in konqueror, in firefox the buttons work fine... Except the web browsers what other programs supported when fwd/back buttons? I want to test them, but i can't think of any programs

---

### Post by jperez on 2007-05-21
If you have the same type of mouse I have (Intellimouse Optical USB and PS/2 Compatible), then use this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection
```

This is exactly what I have and it works perfectly.  I actually stumbled upon this by accident.

I had done the short cut, restarted X and nothing happened.  I then tried xev, but my side buttons were showing as button 2 and 3, so I changed ImPS/2 to ExplorerPS/2 so that I could map the buttons manually.  Well, the guide asked to restart X, so I logged out to restart it again, but it froze up on me, gave me a black screen and forced me to restart my PC.

Upon logging back in, I figured I'd try to use the buttons for the heck of it and they worked perfectly!  My guide ends at changing ImPS/2 to ExplorerPS/2.  That's it.  What you see is exactly what I have in my xorg.conf file, so try it and see if it works for you.

Jesse~

---

### Post by southernman on 2007-05-22
Works like a charm, jperez.

Easier searching the forum for this hack, than digging through the ubuntu docs site(s)

---

### Post by HumbleGod on 2007-05-23
Thanks, changing the protocol did the trick!

---

### Post by Fyrehardt on 2007-05-24
Thank you for this HowTo!  I got side buttons again!  Although, I think the main thing I needed to do was change the protocol to ExplorerPS/2.  Otherwise, it was mapping my side buttons as the same as the main buttons on the mouse.  :KS:KS:KS:KS:KS for you!

---

