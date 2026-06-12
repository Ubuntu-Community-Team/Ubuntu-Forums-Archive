---
title: "Kensington Expert Mouse"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by joemo75 on 2006-07-05
Hi All,

I've been having a ball playing around with Ubuntu 6.06 these past few days.

I'm looking for help with my Kensington Expert Mouse (trackball).  Currently, button 2 is my "right click" button, but I would like to change that to button 4.  Is this possible?  

Thank you

---

### Post by one norse on 2006-07-06
[QUOTE=joemo75]Hi All,

I've been having a ball playing around with Ubuntu 6.06 these past few days.

I'm looking for help with my Kensington Expert Mouse (trackball).  Currently, button 2 is my "right click" button, but I would like to change that to button 4.  Is this possible?  

Thank you[/QUOTE]

Try" System Settings -> Mouse Settings" and switch from right to left handed.

---

### Post by joemo75 on 2006-07-07
Thanks but will change what button one does.  I need to leave button one as-is.  I'm pretty sure I need to muck with xorg.conf - I just don't know exactly what options I need to use and the Xorg documentation hasn't been of any help yet.

---

### Post by thegnu on 2007-07-09
this is a very late reply, but in case and googlers come by, you would use the xmodmap command in .xinitrc, or add it to your gnome startup at System > Preferences > Sessions.

I don't know what the button mappings are, though.

---

### Post by sugarland2k on 2007-07-12
I've got a Kensington Expert Mouse (track ball) on my Kubuntu system and I need to tweek it to get the scroll wheel and all the buttons working.  I have some notes on this out the house and I will dig them up and post them.  

I do have an old thread to see 
[http://ubuntuforums.org/showthread.php?t=448768](http://ubuntuforums.org/showthread.php?t=448768)

Good luck!  "I'll be back" :)

---

### Post by ADH on 2007-11-05
I have a Kensington Expert Mouse - I've used one since I first started messing with computers, as I'm disabled, and the big ball mad scrolling much easier than smaller trackball or regular mouse.  Plus, the Kensington software allowed me to set buttons 3 and 4 as locked down, which I need, as I can't hold down a button and scroll at the same time.  Thus, my question - can I set those buttons to function like that in Ubuntu?  Kensington doesn't have software for Linux, and, when I looked at Accessibility options in Ubuntu, there were options for the keyboard, logging in, etc., but nothing for the mouse.  

Thanks,

---

### Post by ADH on 2007-12-21
Bump...

---

### Post by beppu on 2008-01-31
**[http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse7.html](http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse7.html)**

The Kensington Expert mouse is really a trackball. It has 4 buttons arranged in a rectangle around the ball.

```
[INDENT][FONT="Courier New"]Section "InputDevice"
	Identifier  "DLB"
	Driver      "mouse"
	Option      "Protocol" "ThinkingMousePS/2"
	Option      "Buttons" "3"
	Option      "Emulate3Buttons"
	Option      "Device" "/dev/mouse"
	Option      "DragLockButtons" "2 1 4 3"
EndSection[/FONT][/INDENT]
```

In this example, button 2 is a drag lock button for button number 1, and button 4 is a drag lock button for button 3. Since button 2 is above button 1 and button 4 is above button 3 in the layout of this trackball, this is reasonable.

Because button 2 is being used as a drag lock, it can not be used as an ordinary button. However, it can be activated by using the "Emulate3Buttons" feature. However, some people my be unable to press two buttons at the same time. They may prefer the following InputDevice section which defines button 4 as a master drag lock button, and leaves button 2 free for ordinary use.

```
[INDENT][FONT="Courier New"]Section "InputDevice"
	Identifier  "MasterDLB"
	Driver      "mouse"
	Option      "Protocol" "ThinkingMousePS/2"
	Option      "Buttons" "3"
	Option      "Device" "/dev/mouse"
	Option      "DragLockButtons" "4"
EndSection
[/FONT][/INDENT]
```

---

### Post by rjinator on 2008-05-08
Does anyone know how to change the scroll direction of the scroller?  I use my mouse on my left hand and need to switch the direction...

---

### Post by ADH on 2008-05-24
> **rjinator said:**
> Does anyone know how to change the scroll direction of the scroller?  I use my mouse on my left hand and need to switch the direction...

> **beppu said:**
> **[http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse7.html](http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse7.html)**

The Kensington Expert mouse is really a trackball. It has 4 buttons arranged in a rectangle around the ball.

```
[INDENT][FONT="Courier New"]Section "InputDevice"
	Identifier  "DLB"
	Driver      "mouse"
	Option      "Protocol" "ThinkingMousePS/2"
	Option      "Buttons" "3"
	Option      "Emulate3Buttons"
	Option      "Device" "/dev/mouse"
	Option      "DragLockButtons" "2 1 4 3"
EndSection[/FONT][/INDENT]
```

In this example, button 2 is a drag lock button for button number 1, and button 4 is a drag lock button for button 3. Since button 2 is above button 1 and button 4 is above button 3 in the layout of this trackball, this is reasonable.

Because button 2 is being used as a drag lock, it can not be used as an ordinary button. However, it can be activated by using the "Emulate3Buttons" feature. However, some people my be unable to press two buttons at the same time. They may prefer the following InputDevice section which defines button 4 as a master drag lock button, and leaves button 2 free for ordinary use.

```
[INDENT][FONT="Courier New"]Section "InputDevice"
	Identifier  "MasterDLB"
	Driver      "mouse"
	Option      "Protocol" "ThinkingMousePS/2"
	Option      "Buttons" "3"
	Option      "Device" "/dev/mouse"
	Option      "DragLockButtons" "4"
EndSection
[/FONT][/INDENT]
```



What do I do with the code I choose?  I presume I edit a config file, so where do I find that file, and what's a good editor to use?

Thanks,

---

### Post by jaygo on 2008-07-10
@ADH
these go into /etc/X11/xorg.conf

Be careful making changes as you can easily disable your system. For GUI editors, you can run ```
kdesu kate /etc/X11/xorg.conf
``` or ```
gksu gedit /etc/X11/xorg.conf
```

@rjinator
you should be able to swap the ZAxisMapping buttons to change the scroll direction. Just use what I have below and change it to "5 4". Note, I haven't tested that and am only making a logical assumption.

My "expert mouse" worked out of the box. But I'm changing the button mapping to swap buttons 2 & 4:

```

Section "InputDevice"
	Identifier	"Kensington Expert Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Device"	"/dev/input/mice"
	Option		"Buttons"	"6"
### button order seems to change depending on buttonmapping sequence
### the following sets left-click lower-left, right-click upper-right, button4 lower-right, middle-click upper-left
	Option		"ButtonMapping"	"1 2 6 3"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

Also, under Section "ServerLayout", I've added
```

	Inputdevice	"Kensington Expert Mouse"	"CorePointer"
```

---

