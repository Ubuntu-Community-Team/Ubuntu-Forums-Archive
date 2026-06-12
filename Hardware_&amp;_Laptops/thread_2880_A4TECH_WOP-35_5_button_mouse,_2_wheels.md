---
title: "A4TECH WOP-35: 5 button mouse, 2 wheels"
date: 2004-11-01
forum: Hardware &amp; Laptops
---

### Post by tanari on 2004-11-01
how get "back" and "forward" buttons to work?

---

### Post by Phreneticus on 2004-11-01
I don't know if it works but u could try [this](http://www.linuxforum.com/linux_tutorials/70/1.php) .

---

### Post by adbak on 2004-11-01
I tried that link to the best of my ability and it ended up breaking my X.  Luckily I had Knoppix on hand to mend my mistakes (backups of files I had changed helped too).

---

### Post by Peti29 on 2007-02-06
I happen to have an A4Tech WOP-35 too. It took some searching and then some experimenting until I came up with the following settings which seem to work for me.
The out of the box behaviour of my mouse was that side buttons didn't work and both wheels did the same: scrolling vertically. However the "upper" wheel (the one that is not click-able) scrolled twice as fast as the other.
After my modifications the side buttons are alive, the "lower" wheel scrolls nothing (the click functionality is still OK), and the "upper" wheel scrolls normally in vertical directions (that is not double-speeded).
For me the "lower" wheel is a bit too far away, the "upper" one fits into my hand better so I don't really care that the "lower" wheel became dead.
I did the following:

```
sudo gedit /etc/X11/xorg.conf
```
Modify the section "Input Device" which is about mouse so that it looks like this:
```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "6 7 4 5"
	Option      "Buttons" "9"
EndSection

```

After that open up System/Preferences/Sessions. On the tab page "Startup programs" add 
```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
```

Press Ctrl-Alt-Backspace to restart X.

---

### Post by Talito on 2007-05-03
I did exactly as you said, changing the xorg.conf, and the Back/Forward buttons started working perfectly. But none on my mouse wheels work now, what should i do?

---

### Post by numnutz on 2007-05-21
I have got my A4tech 35 working with back and forward buttons, also the front scroll wheel is working as it should. (the back scroll wheel is dead) 

this is what i used

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
    	Option 		"Buttons"	   	"9"
    	Option 		"ButtonMapping"		"1 2 3 6 7"
EndSection

---

### Post by mesilliac on 2007-09-11
I have this mouse connected via USB, and found the Gentoo Linux guide to setting up mice very helpful. [http://gentoo-wiki.com/HOWTO_Advanced_Mouse](http://gentoo-wiki.com/HOWTO_Advanced_Mouse)

The InputDevice section for my mouse in /etc/X11/xorg.conf is
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name" "A4Tech USB Optical Mouse"
EndSection

```

The "Name" option is important. To find out what it should be, open a terminal and type
```
cat /proc/bus/input/devices
``` then look for the "Name" entry corresponding to your mouse. The option in xorg.conf should match this name exactly.

After setting this and restarting X all the mouse buttons should just work, but you still might want to play around with the xmodmap command to swap buttons around. I like to have the horizontal scroll direction reversed, and also I use the thumb button as a middle mouse button so I added the following command to my startup session: ```
xmodmap -e "pointer = 1 8 3 4 5 7 6 2 9"
``` Follow the link above for more info about using xmodmap.

---

### Post by Muni Beduhin on 2008-01-15
July 15 08
Mesilliac--

      Much thanks. I have a only two mouse buttons on mine, but I do have the two scroll wheels. A friend had been telling me about how he got his double-scrolling mouse to do the horizontal and vertical scroll thing on Windows, and I have been getting fed up with having a useless button on my mouse! Anyhow, per your instructions, my mouse seems to be working well now (I haven't actually restarted KDM, but I launched a separate X session and started Gimp, and it worked there.)
    
    Changing the driver from mouse to evdev and doing the name parameter to tell it it was a A4 Tech Optical seemed to be the important things.
    
    Thank God for Linux!
                          --Muni Beduhin

---

### Post by GreatStarMaster on 2008-03-24
Tell me please what i need to change in this settings if i want side buttons working like copy and paste.

---

