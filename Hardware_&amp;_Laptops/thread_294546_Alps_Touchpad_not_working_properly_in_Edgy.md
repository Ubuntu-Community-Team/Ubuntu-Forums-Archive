---
title: "Alps Touchpad not working properly in Edgy"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by akarimco on 2006-11-06
Using Dapper, the Alps touchpad on my Vaio v505ex always worked perfectly fine.  Upon upgrading to Edgy, it worked fine for a couple days and then randomly began to have problems.  I reformatted and installed a clean copy of Edgy and the same thing happened again after a few days.  The touchpad suddenly moves at an incredibly slow speed, requiring me to run my finger across it about 6 or 7 times to make it across the whole screen, and scrolling won't work.  I've tried changing settings using gsynaptics and qsynaptics with absolutely no change.  My touchpad is now almost useless and I'm forced to use an external USB mouse to navigate my computer.  I can only hope someone can come along with a solution before I end up running back to Windows.  I just want this darn thing to work! ](*,)

---

### Post by Aielyn on 2006-11-11
I've got the same problem. I upgraded from Dapper to Edgy yesterday, and today, for seemingly no reason, the touchpad went strange, just as you describe (requires me to run my finger over it many times to get across screen, scrolling won't work). Using gsynaptics, I tried setting the sensitivity to maximum, to no avail.

Fortunately, my laptop (which is a Toshiba Tecra M2) has a mouse nub on the keyboard, so I can still move around without the touchpad... but it's a major nuisance, especially because I've become very used to using the touchpad and its scrolling function.


EDIT: It appears that the problem is an issue of scaling - it's as though the "virtual" touchpad is about four times the size of the physical one, and the physical one covers only the top-left corner. This would explain both the lack of scrolling (which works on the right and bottom edges of the virtual touchpad), and the slow motion of the mouse. Also, it would explain what I have observed when I select "cursor movement" in the "on an edge" section of the "scrolling" tab of gsynaptics (when selected, touching the touchpad acts as though you are touching the top-left corner, causing the "mouse" to move up and to the left).

---

### Post by Aielyn on 2006-11-11
OK, I may have found a temporary solution to this problem.

I tried switching xserver-xorg-input-synaptics with xfree86-driver-synaptics. It appears to have fixed the problem of the scaling, although the scrolling is still not working, and it is overly-sensitive to tapping. Also, the sensitivity is controlled through the "mouse sensitivity" settings found in System>Preferences>Mouse.

Unfortunately, neither gsynaptics nor qsynaptics will work with the xfree86 version.

I am still trying to reinstate the remaining functions.

EDIT: I have now tried switching back to the xserver version, and the problem has returned. This indicates that xserver-xorg-input-synaptics is where the fault lies.

---

### Post by Aielyn on 2006-11-11
OK, new information. (assuming it has xserver-xorg-input-synaptics, and not xfree86-driver-synaptics)

If you type "synclient -l" into a terminal, it will output a set of details about the touchpad. Look specifically at the first four - "LeftEdge", "RightEdge", "TopEdge", and "BottomEdge". You will most likely find that all four numbers are over 1000.

What you want to do is type "synclient LeftEdge=0", then "synclient TopEdge=0" into the terminal, then try some numbers for RightEdge and BottomEdge (I used RightEdge=840, which seems to work very well, and BottomEdge=500, which doesn't seem to matter too much).

What you want to do is select your RightEdge value so that you can scroll if you run your finger along the right edge, but nowhere else. If the value is too large, it will not scroll. If the value is too small, it will scroll too far in on the touchpad. The BottomEdge value would matter if you were to implement the horizontal scrolling, and would be determined in the same way.

Now, that fixes scrolling, but you still need to correct the sensitivity. To do this, you need to change the "MinSpeed", "MaxSpeed", and "AccelFactor" values to suit. For me, MinSpeed was set to 0.09, MaxSpeed was set to 0.18, and AccelFactor was set to 0.0015. I changed these to 0.25, 0.5, and 0.005, respectively, and it seems to work nicely for me. As before, you type "synclient MinSpeed=0.25" into the terminal to change it.

These changes should happen instantaneously, so you should immediately be able to see the effects.

I have yet to try rebooting the X-server or the system, so I do not yet know if these changes are persistent, or if I need to find a config file for this to make it happen automatically every time. I will update following a reboot.

UPDATE: Well, it's not persistent. It seems these values must be put into xorg.conf, which I will try now.

UPDATE 2: Success - you must insert these parameters into xorg.conf. You insert them into the "Touchpad" section, in the form:
Option    "LeftEdge"    "0"
Option    "MaxSpeed"    "0.5"
and so on.

Now, my touchpad is working normally again (although, I may still need to alter the sensitivity of scrolling). Hope this helps you, too.

---

