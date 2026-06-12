---
title: "mousepad scroll (scrolling) problem"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by elmasto on 2007-07-19
I have a gateway laptop with Ubuntu 7.04.
A slight inconvenience with the mousepad...
My mousepad has a separate vertical scroll area, that is working great. But it seems like Ubuntu has rendered about a quarter of the 'normal' mouse pad area to function as vertical scroll bar, so essentially I have about a third of the entire mousepad just for scrolling....and it is a bit annoying.
Any help?

---

### Post by jonlemur on 2007-07-20
I have a Gateway Laptop (M460 I think), and it has a mousepad just like you described.  I got the scrolling to work just like you want.  Here are the programs I used, followed by an explanation of how I used them.  The first two should be included by default.  If not, you'll have to install them.

synaptics
synclient
gedit (or you favorite text editor), for editing /etc/X11/xorg.conf
gsynaptics (I don't think this one was necessary, but it makes it easy to edit some features, like touch sensitivity)

The synaptics one is the most important.  If you do a man synaptics, it will tell you all of the things that you can edit about your touchpad.  To use the commands you will find, you need to edit your /etc/X11/xorg.conf file.  Open it and find the section 

> 
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"

Under that you will find several lines of 
Option    "OptionName"    "OptionValue"

You will need to insert the lines
> 
	Option		"RightEdge"		"8100"
	Option		"VertEdgeScroll"	"true"

Run "man synaptics" to find out descriptions of the two options.  It will also give you a hint for how to find what value you should use for "RightEdge."  This is basically run
> synclient -m l
in the terminal, and determine where you want the right boundary to be.  The x coordinate of where you are touching should be the second number listed as you are using the touchpad (there should be a header that says which one is the x coordinate).  I wound up putting the maximum (or nearly the maximum) value that I got with my finger to the far right. 

And if you want a graphical way to adjust scroll speed, touch sensitivity and a few other similar things with the touchpad, also include 
> 	Option		"SHMConfig"

and run 
> sudo apt-get install gsynaptics

Restart the X server (Ctrl+Alt+Backspace) and run gsynaptics in the terminal to open a GUI.

I hope that helps.
Cheers

---

### Post by jonlemur on 2007-07-21
My apologies, you don't want the maximum value of the x coordinate.  When I did that, I must have not restarted the X server.  What you want (for the value of the 'Option "RightEdge" "Value"' is the right-most part that you want to function as the regular touchpad, or the left-most part that you want to function as the scroll area.  For me, this turned out to be about 5900.  Also, I think now that you may need to have gsynaptics installed and include the line 

Option "SHMConfig"

And you may need a "true" to follow that.  I think just having the line without the boolean is the same as having the line with "true," but I could be wrong.  Below is an excerpt from my xorg.conf file.

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"RightEdge"		"5900"
	Option 		"VertEdgeScroll"	"true"
EndSection


---

