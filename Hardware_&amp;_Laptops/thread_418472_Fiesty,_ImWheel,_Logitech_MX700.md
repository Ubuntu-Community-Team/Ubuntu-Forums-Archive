---
title: "Fiesty, ImWheel, Logitech MX700"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by klytu on 2007-04-22
Attempting to get extra buttons working on my Logitech MX700 mouse (connected to a PS2 port) while running Fiesty, I followed [[COLOR="Red"]_the instructions here_[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox"). However the buttons did not respond properly in either Firefox or Nautilus when ImWheel was running. To correct I changed the file /home/login/mouse from this (which works fine in Dapper): > #!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP to this:>  #!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 6 7" &
exec imwheel -k -b "6 7" &
exec $REALSTARTUP then, I rebooted and the extra mouse buttons worked as expected in both Firefox and Nautilus.

---

### Post by dmanbuhnik on 2007-10-13
i got the wireless set lx710 with the mouse lx700 and i'm using 7.04 too so this should work for u as well
this is my config (working like a charm!)

xorg.conf:
> Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Buttons" "10"
EndSection
don't ask me why 10 button while we have only 9, i don't know but its working
and i added to the startup:
> xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"

all the mouse buttons in this way are working

i also added to the imwheel config file those lines (i want the thumbs button to change tabs and not to go back and forward):
> "^Firefox-bin$"
# Flip between browser tabs
None, Thumb1, Control_L|Page_Up
None, Thumb2, Control_L|Page_Down

have a good one,
mmm, maybe you can help me - do u know how to set the tilt action to do a button action using imwheel (i want to tilt to be tilt in all the windows but in FF i want tilt to change tabs, this would be very easy if only imwheel knew what tilt action is :( )

---

