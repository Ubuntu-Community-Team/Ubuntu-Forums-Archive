---
title: "Logitech MX1000 Mouse Switches Buttons Every 3rd Boot"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by nickspoon on 2007-05-03
I have a Logitech MX1000 USB wireless mouse. In Dapper and Edgy, it seems to have worked perfectly well. Since installing Feisty, however, I have encountered a very odd problem. There are two buttons on the side of the mouse - previously, in Dapper and Edgy, they were buttons 9 and 8. And on two of three boots on Feisty, they are also 9 and 8. However, on every third boot, they switch to 7 and 6 (I have checked with xev, this is definitely happening), so I have to change my Beryl options every third boot, which is becoming infuriating. I don't know why this could be happening, but advice would be helpful.

The "evdev" driver is set in xorg.conf for this mouse.

Thanks in advance.

---

### Post by merlinus on 2007-05-03
I can't answer your question, but I have the same mouse.  It works fine, but the side-to-side scrolling feature does not work in ubuntu as it does in win2000.

So.... please explain how you set up the evdev driver in xorg.conf?

The mouse portion of mine is:
> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Many thanks!

-merlin

---

### Post by nickspoon on 2007-05-04
My xorg.conf section looks like this:

```
Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB RECEIVER"
EndSection
```

The side-to-side scrolling works, but in reverse, so tilting the wheel to the left makes the page go right. I think that can be fixed by using:
```
Option          "HWHEELRelativeAxisButtons" "7 6"
```

Only evdev supports horizontal scrolling here, so "mouse" doesn't work.

---

### Post by merlinus on 2007-05-04
Hi, and thanks for responding.

What, and where might I obtain, the evdev driver?

When I changed xorg.conf to reflect the changes you suggested, x would not start.  Fortunately I had made a copy of xorg.conf, so was able to rename it from the CLI.

-merlin

---

### Post by Miguel on 2007-05-08
Your X.org is probably failing to start because you probably didn't update the server layout. If you edit /etc/xorg.conf again, you will find something like this:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

However, in your mouse config you had this:
```
Section "InputDevice"
        Identifier      "Logitech MX1000"
...

```

So, when loading, X looks for a device called "Configured Mouse" (or similar). It won't find any, because your mouse is called "Logitech MX1000". You could try again by making sure you are calling the devices by their correct name. Of course, do a backup of your woking xorg.conf like before ;)

---

### Post by merlinus on 2007-05-08
I followed your suggestions, but it still crapped out upon reboot.  Had to go back to my original xorg.conf.

Thanks anyway....

-merlin

---

### Post by Subban on 2007-05-31
I have been trying to resolve this very same issue with the same mouse, my experience leads me to feel it just switches the buttons on each boot, on minute its mapped to 9 and 8, next boot 7 and 6.

has anyone managed to sort this or any insight ?

---

