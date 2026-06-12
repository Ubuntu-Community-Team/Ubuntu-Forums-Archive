---
title: "PS/2 Mouse Wheel Help"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by itchanddino on 2006-09-07
I'm running the latest version of Xubuntu.
So, my laptop only has 2 usb ports.  I have one for ethernet and the other I plugged my USB mouse into it (I got sick of the touchpad) and it worked fine and dandy.  But I got a pendrive, so to spare some calories I plugged my mouse into one of those usb to ps/2 converters so that I have an open USB port.  However, after making this change, my mouse wheel will no longer work.  I can use it as a 3rd button just fine, but scrolling doesn't work.  I tried editing my xorg.conf file a couple times but to no avail.  Does anyone know specifically what I need to change in that file to make it work?  I read the howto and it didn't help. It is a Logitech mouse that has 3 buttons on it.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

I tried adding Option "Buttons" "5" but it didn't work.  Thanks for any help!

---

### Post by dannyboy79 on 2006-09-08
i am a newbie but just by reading your xorg.conf file, wouldn't you want to change the setting, Option "Emulate3Buttons" "true" to be "false" that way the wheel will be a wheel instead of a "button". Like I said I am just guessing as it makes logical sense that that may be the solution but as I have found sometimes the logical solution isn't the correct one in linux. Good luck and sorry if I wasn't able to help you more. did you gogle, usb/ps/2 adapter wheel function in linux?

---

### Post by itchanddino on 2006-09-08
No, that just makes it so that if you click buttons 1 and 2 it emulates a click on 3.

---

### Post by dannyboy79 on 2006-09-08
oh, too bad. I thought maybe I was on to something. I wish I could help more, you should be able to find plenty of threads if you use the search function and type in "mouse wheel"

---

### Post by itchanddino on 2006-09-08
I have, nothing has fixed it yet though.  Oh well.

---

