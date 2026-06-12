---
title: "[SOLVED] How to emulate scroll with two button mouse?"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by mikespug on 2007-12-20
Good morning!  I'm currently running Ubuntu Gutsy 7.1 on a HP nc2400 laptop.  The laptop comes equipped with a synaptics "touchstyk" (similar to an IBM Thinkpad trackpoint)  with no touchpad and only two mouse buttons.  I prefer the touchstyk to touchpads however I miss the third "scrolling" mouse button that IBM Thinkpads have.  I'm looking for a way to emulate a mouses scroll option using the two buttons provided.  More specifically I'd like to be able to press and hold both mouse buttons simultaneously to scroll.  I've been searching the forums and haven't been able to come up with a solution.  Any help would be greatly appreciated.  Thank you in advance!

Also, If anyone knows how to enable tap to click on this particular setup perhaps I can kill two birds with one...umm.....err....post?   :)

---

### Post by mikespug on 2007-12-27
bump

---

### Post by klausner on 2008-03-28
Is there a *useful* answer to this problem? I've got a MoGo mouse, which is increadibly cool for traveling, but I really miss being able to scroll things.
](*,)

---

### Post by mikespug on 2008-03-31
I suppose I can mark this one as solved since I found a solution that works for me.  Hopefully others will stumble upon this as well.  The following xorg.conf mouse settings allow you to press and hold the right mouse button to scroll and still keep right mouse click functionality.  Edit the EmulateWheelTimeout to increase/decrease time before scroll is enabled (in milliseconds).  The 200 ms buffer allows time to press/depress the button to use the button as normal.  Just keep in mind that if you set the number to too small a value you will loose right mouse click functionality as you can only press and release the button to select so quickly.

For those who have never played with it...open up a terminal and use your favorite editor to edit the following file as root:

/etc/X11/xorg.conf

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"EmulateWheel"		"True"
	Option		"EmulateWheelButton"	"3"
	Option		"EmulateWheelTimeout"	"200"
	Option		"XAxisMapping"		"6 7"
	Option		"YAxisMapping"		"4 5"
EndSection
```

Hope it helps!

---

### Post by klausner on 2008-03-31
Wouldn't this interfere with the ability to highlight or select blocks of text?

---

### Post by mikespug on 2008-04-01
If I am understanding you correctly the actions you are referring to are usually performed using the *left* mouse button.  (Depress left mouse button...hold....drag to highlight.)  With the EmulateWheelButton enabled on the right mouse button (button 3) you get normal behavior from the button until it is depressed for more than 200ms (2 seconds) when it enables the scroll emulation.  I suppose I should also mention that users need to pay particular attention to the X and Y AxisMapping settings that I have listed.  These are the settings that I use to ensure proper vertical/horizontal scrolling on my laptop. (i.e. press up and page scrolls up/ press left page scrolls left) If you find that you move the mouse up and it goes down simply reverse the values.

---

