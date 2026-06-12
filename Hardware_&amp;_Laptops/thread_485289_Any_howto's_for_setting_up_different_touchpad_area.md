---
title: "Any howto's for setting up different touchpad areas?"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by Bazirker on 2007-06-26
My laptop, like many these days, has two separate areas on the touchpad: a big area for moving the mouse around, and then a small, vertical area on the right used for scrolling.  In Windows, this is taken care of via the manufacturer's device drivers, but in Feisty, those drivers are no good.  Is there any method for configuring this?  As of right now, if I touch the scroll area, it makes my cursor jump across the screen and it's a major pain, not to mention I really like having the scrolling function...any tips?

---

### Post by sr20ve on 2007-06-26
I have a similar issue with my Dell laptop, however, my scroll section of my touchpad works, but I don't realy like how it works, it's too touchy and scrolls too fast, I'd like to just disable it. It's also annoying, because if you touch that portion of the touchpad while on the desktop, it switches between your different desktops.

Is there a way to either disable that scroll section of your touchpad, or at least unassign the hot key that makes it switch between desktops? BTW this is on Feisty as well.

---

### Post by speaker219 on 2007-06-26
You can configure settings like this with an add-on for ubuntu called "gSynaptics."
first, run this command in terminal:
```
sudo gedit /etc/X11/xorg.conf
```
Look for a line that says "Synaptics Touchpad" and add "SHMConfig" "on" so it will look something like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
EndSection
```
(It may seem hard but just add one line to the section for your touchpad)
then save the file and exit.
Push Ctrl+Alt+Backspace to restart X
then open a terminal again and run the following command:
```
sudo apt-get install gsynaptics
```
this lets you configure many things with the touchpad including whether tapping is enabled, horizontal/vertical scrolling and other helpful things. enjoy!
EDIT: here are some screenshots of the settings you can change in the tool: (click to enlarge)
[[img]http://xs116.xs.to/xs116/07263/oneone.png.xs.jpg[/img]](http://xs116.xs.to/xs116/07263/oneone.png) [[img]http://xs116.xs.to/xs116/07263/oneonetwo.png.xs.jpg[/img]](http://xs116.xs.to/xs116/07263/oneonetwo.png) [[img]http://xs116.xs.to/xs116/07263/oneoneonethree.png.xs.jpg[/img]](http://xs116.xs.to/xs116/07263/oneoneonethree.png)

---

### Post by Bazirker on 2007-06-27
That looks great! Unfortunately, I checked xorg.conf and I don't have a synaptics touchpad showing up.  I have:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection
```

Configured Mouse is my MX1000, and the stylus, cursor, and eraser all use the wacom driver.  Any ideas?  Thanks!

---

### Post by speaker219 on 2007-06-27
Hm, I don't know, maybe if you go back into windows and find out the model /brand of your touchpad I might be able to help... (or if you could remember)

---

### Post by pedrogl on 2007-06-27
X server must be autodetecting your touchpad, so you can just copy the InputDevice section as pointed by speaker219, an add a new line to your ServerLayout like these:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad" "SendCoreEvents"
EndSection
```

---

### Post by Bazirker on 2007-06-27
I'm using a Synaptics TouchPad V6.1 in my Asus Z96J notebook.  Pasting in the code, restarting X, then installing gsynaptics did the trick!  I just had to go mess with the settings in System > Preferences > Touchpad to get things working how I wanted.  Is there any way to change the area of the touchpad alloted to scrolling?

Thanks speaker 219 and pedrogl!

---

### Post by pedrogl on 2007-06-27
I've never used gsynaptics, but maybe it's a graphical frontend of synclient. With synclient you can specify many options. For example:
```
synclient CircularPad=1
```
Activates nice circular scrollpad.
Later you can edit your xorg.conf and add the line:
```
Option "CircularScrollPad" "1"
```
In the InputDevice section in order to make permanent the option.

Options you're looking for should be LeftEdge, TopEdge, etc. Take a look at the man page of synaptics and synclient for a better explanation:
```
man synaptics
man synclient
```

---

### Post by pompom246 on 2007-07-03
Hi, I just set up my first linux installation on my HP laptop and put in gsynaptics for my touchpad. Everything seems to work well except for the fact that the right scrolling field in the touchpad is much larger and takes up about 33% of the total touchpad area. I was able to configure the area back in my Windows days, but is there any way to do this in Ubuntu?

---

### Post by Bazirker on 2007-07-08
Yeah I think there's a way...look through the "man synaptics" thing that pedrogl mentioned.  I looked briefly and I think there's something in there that tells you have to define the different areas of your touchpad, although it isn't through a GUI setup, only command line.  You change the integer values to manipulate this:

```
       The LeftEdge, RightEdge, TopEdge and BottomEdge parameters are used  to
       define the edge and corner areas of the touchpad.  The parameters split
       the touchpad area in 9 pieces, like this:

             |             |
             | LeftEdge    | RightEdge
       +-----+-------------+---+ Physical top edge
       | 1   |      2      | 3 |
       +-----+-------------+---+ TopEdge
       |     |             |   |
       | 4   |      5      | 6 |
       |     |             |   |
       +-----+-------------+---+ BottomEdge
       | 7   |      8      | 9 |
       +-----+-------------+---+ Physical bottom edge
       |Physical left edge     | Physical right edge
```

I have no idea what value integers to put it, but try some stuff and let us know what works!  Hope this helps some...

---

### Post by pedrogl on 2007-07-08
Hi, Bazirker is right. Try using synclient for monitoring your tp:
```
synclient -m 500
```
This way you can obtain the correct values for your hardware (use CTRL-C to quit synclient when you are done).

---

### Post by Bazirker on 2007-07-09
I just used synclient to test my touchpad, and it appears that my touchpad is physically divided not in software but in hardware into two seperate areas.  If I put my finger on the left side of the touchpad and slowly slide it to the right, it starts at "0" and it increases till I hit roughly "5980," then everything to the right of that point is "8176."  This area is roughly a a centimeter and a half wide and, in just the perfect light, appears to have a faint vertical line dividing it from the main area of the touchpad.  Looks like I'm stuck with a set touchpad area!  Bah!  I think I might put down some physical barrier (like a thin piece of tape or something) to give me a tactile clue that I'm going to be entering that area with my finger so I stop mousing around into suddenly scrolling all over the place.  (For anyone who's concerned, Windows tells me I have a Synaptic V6.1 touchpad on my Asus Z96J notebook.)

---

### Post by buntunub on 2007-07-16
Hey thanks for this guide. Fixed up my scrollbar; thats been really nagging me ever since I installed Fiesty!

---

