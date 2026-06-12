---
title: "Synaptics"
date: 2008-04-26
forum: Hardware
---

### Post by nago on 2008-04-26
Hi, I'm running the newest Ubuntu (8.04 I believe?) although this issue should be relevent to all recent releases.

I have a Synaptics Touchpad on my laptop (Gateway of some sort, MT6707?) that is not working as expected in ubuntu.

Physically, the left 80% and the right 20% are segmented by a small ridge. The right side is meant to scroll, the left is for regular cursor movement.

The division doesn't seem to be picked up correctly in ubuntu however, leaving 10-20% of the "main" cursor area allowing scrolling movement.

I tried installing gsynaptics, ("touchpad" under System > Preferences) but it doesn't seem to have any options for calibration of this sort.

Any hints?

---

### Post by ricardomcl on 2008-04-27
Hi!

I think I can help you with that because I had the same issue.

I solved it editing the /etc/X11/xorg.conf file.

EDIT (I forgot to mention it the first time I wrote this): 
[COLOR="Red"]**IMPORTANT NOTE:**[/COLOR] Before you do any changes to this file, it is best to make a backup copy of it.
Open a terminal window and type this command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ORIG
```
This is to ensure that you have a recovery option, in case things go bad. If, for any reason, your Ubuntu doesn't start correctly after editing this file, you can always reverse your changes with:
```
sudo cp /etc/X11/xorg.conf.ORIG /etc/X11/xorg.conf
```
on a console (eg. CTRL-ALT-F1)
[COLOR="Red"]**END OF NOTE**[/COLOR]
Now we can continue...

Open the file with
```
sudo gedit /etc/X11/xorg.conf
```

Locate the section of the synaptics touchpad in that file.
It should look like this:
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection
```

Add this line  inside that section:
```
    Option	"SHMConfig"	"1"
```

Then save it, close it and restart X (eg: with CTRL-ALT-BACKSPACE)

After restarting execute
```
synclient -m 1
```

Use your touchpad and place your finger on the place you want the main cursor area right limit to be. Take a note of the value of the X column.
Press CTRL-C to stop it.

Now open the above file again and add the following line inside the same section
```
Option	   "RightEdge"	"XXXX"
```
Replace XXXX with the value you wrote down.

Save the file, close it, and restart the X-server again.

Use your touchpad and see if it's better. If not, change that XXXX value until you find one that suits your needs. Mine was 5950, but yours may be different because not all touchpads are the same.

You have many other options to set for your touchpad. In case you want to explore those, use the manual for synaptics:
```
man synaptics
```

Prepare some :popcorn:

;)

I hope you find this helpfull.

---

### Post by nago on 2008-04-27
That seemed to have done the trick!

Thanks a bunch :D

---

### Post by baucha_linux on 2009-03-05
sorry for reviving dead thread but I was wondering how can this be done in Itrepid 8.10 as I understand that xorg.conf is no longer used to control devices. I am in Kubuntu 8.10.

I would be very grateful if someone can shed lights on this. Moreover, this post wud be updated as well ;)

---

