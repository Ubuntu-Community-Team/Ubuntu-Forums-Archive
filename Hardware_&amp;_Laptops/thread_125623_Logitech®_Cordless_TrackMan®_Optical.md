---
title: "Logitech® Cordless TrackMan® Optical"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by floff on 2006-02-04
Hello folks.

I have the last week been trying to find the correct configuration for me to use on my Logitech® Cordless TrackMan® Optical, since the forward & back button won't work. The Trackman has to my eye the exact same button layout as the Logitech MX 510, so I tried this guide: ([http://ubuntuforums.org/archive/index.php/t-65471.html](http://ubuntuforums.org/archive/index.php/t-65471.html)) with no result. As far as I can see it all boils down to one point, being the Xmodmap answering "xmodmap:  /home/tobias/.Xmodmap:1:  bad number of buttons, must have 5 instead of 10
xmodmap:  1 error encountered, aborting." to being put to "pointer = 1 2 3 6 7 8 9 10 4 5"

However xev does not recognize more than five buttons, 4 and 5 being scroll wheel turned up and down. Forward button  has the same xev output as the ring finger button (equals Right MB on the MX 510), and the button for scrolling upwards (not wheel scroll), wheel click and the back-button shares output. 

At first I was determined not to bother anyone with this, using google and just testing (resulted in two or three X crashes) because it's way more easier to learn how stuff works that way. But now I just don't have  a clue. Please help me before I go back to windows again (really, really don't want that).

Trivia:
Using the xbindkeysrc with:
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:7"
gives me nada, but replacing 6 with 2 and 7 with 3 got my forward & back-buttons working correctly, losing my right click menu and the "open link in new tab in firefox with the scroll wheel" function.

Xorg.conf:
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol" "evdev"
	Option		"Dev Name" "Logitech USB Receiver"
	Option		"Dev Phys" "usb-*/input0"
	Option		"Device" "/dev/input/event3"
	Option		"Buttons" "10"
	Option		"ZAxisMapping" "4 5"
EndSection

It is unclear how much gratitude I would feel if someone would help me solve this, but infinite comes to mind...

---

