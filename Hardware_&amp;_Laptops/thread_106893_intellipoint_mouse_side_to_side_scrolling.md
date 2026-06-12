---
title: "intellipoint mouse: side to side scrolling"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by timczer on 2005-12-21
I have searched this and googled it, tried several things from google to make it work, but to no avail.  Most of the info on the web is not debian or ubuntu.  I have a new optical intellipoint mouse.  It has two left side buttons, and a scroll wheel that will move left and right as well as up and down, which I guess means that technically it has 9 buttons.  I would like all of these buttons to be useful, but especially the left and right scroll.  I do a lot of work with spreadsheets and this would be great to have.

Has anyone got this working on ubuntu and can let me know how or point to a tutorial that worked for them?

---

### Post by roycrom on 2005-12-22
Well wheel mouse scrolling is set in the xorg.conf by using "Option" "ZAxisMapping" "4 5" so I imagine that the left right scrolling will be similar - I don't know if it will be XAxisMapping or YAxisMapping and I don't know if it will be "6 7" or "8 9" for the button numbers.  There are only four combos for that, you could try them all.  By the way, this is just an educated guess - I couldn't really find anything either, hope this helps.

---

### Post by timczer on 2005-12-22
Still no progress on the side to side.  I have "buttons" option in xorg set to "9" buttons.  Through running xev, I can see that up is 4 and down is 5 on the scroll wheel.  I can not get xev to see the left or right of the scroll wheel.  It also shows that the two side buttons are 6 and 7 and then the normal top buttons are 1 and 3 with the press of scroll wheel being 2.  How do I get my system to recognize the 8 and 9 buttons and use them for side to side scrolling.

---

### Post by timczer on 2005-12-23
Any help with this?  It is a MS intellipoint 5.3 mouse.  I have googled this and haven't found anything that works for me.  I tried changing the "protocol to "intellipoint" and that messed up the mouse so it didn't work.  "ExplorerPS/2 seems to work fine.  Is there a different protocol to try?  I have read several posts about using imwheel, but others that say it isn't necessary to get all nine buttons working.  If imwheel is the way to go, is there clear howto on how to set it up in ubuntu.  Thanks for any help anyone can give.

---

### Post by timczer on 2005-12-27
Any possible words of wisdom on this?  For more info, here is my current xorg.conf section on the mouse: 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"		"4 5"
	Option		"Resolution"		"1000"
EndSection

Any help would be great. Thanks

---

### Post by Joey French on 2006-02-12
I am looking for advice on this as well, with my Microsoft Wireless Mouse 2.0, with L-R buttons.

Maybe someone will chime in...?

Joey French

---

### Post by Rizado on 2006-02-12
I don't now if this is gonna help you but try to use evdev driver instead. Instructions can be found [here](http://www.ubuntuforums.org/showthread.php?t=65471)
This should atleast fix any problems with too many buttons, but you'll probably have to play with it for a while to get scroll and everything working.

---

