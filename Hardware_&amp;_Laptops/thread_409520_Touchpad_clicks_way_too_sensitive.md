---
title: "Touchpad clicks way too sensitive"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by royrules22 on 2007-04-14
Hi,

The touchpad on my laptop is just way too sensitive. Whenever I'm typing my thumb usually hovers over it and it occasionally touches the touchpad. Such a small touch usually ends up being a click and totally ruins what I type or at best kills the momentum. Also I cant really use the touchpad as a mouse since it ends up clicking everything I go over. Is there any way I can make the clicks less sensitive or atleast turn off the damn touch clicking..?

---

### Post by royrules22 on 2007-04-15
bump

---

### Post by mojoman on 2007-04-15
> **royrules22 said:**
> Hi,

The touchpad on my laptop is just way too sensitive. Whenever I'm typing my thumb usually hovers over it and it occasionally touches the touchpad. Such a small touch usually ends up being a click and totally ruins what I type or at best kills the momentum. Also I cant really use the touchpad as a mouse since it ends up clicking everything I go over. Is there any way I can make the clicks less sensitive or atleast turn off the damn touch clicking..?

I *think* you can adjust this by editing your xorg.conf but the configuration probably depends on what touchpad you have. I had to tweak my touchpad (using synaptics) in order to give it a workable speed (its default was *really* slow on Debian Etch). Now, the synaptics touchpad have parameters called "FingerLow" and "FingerHigh" which are given as integer (in plain english I think integer would translate to a numeric value but hey, I from Sweden, what do I know?). This determines the amount of pressure needed for a touch to count as a click. I believe there's also an option to turn off the click-funtion on the touchpad. I've never needed to bother with this specific setting so I can't give you any values but trial and error shouldn't take to long, once you know where to tweak.

If you have a touchpad supported by synaptics make sure you have the correct driver installed (it's called "xserver-xorg-input-synaptics"). There are also graphical configuration tools, e.g. ksynaptics or qsynaptics for KDE and Gnome but I've never used them so I can't say if they'll adjust touch sensitivity as well. A search, ```
apt-cache search synaptics
``` will get you a list of synaptics packages. Also, ```
man synaptics
``` will give you a fairly good explanation of the parameters and options.

If this doesn't help post back with some more info and I'll see what I can come up with.

Best regards 
/Mojoman

---

### Post by mojoman on 2007-04-15
BTW, have a look at these threads as well:

[http://ubuntuforums.org/showthread.php?t=332035](http://ubuntuforums.org/showthread.php?t=332035)

[http://ubuntuforums.org/showthread.php?t=373323&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=373323&highlight=touchpad)

(especially post #2 on the last thread).

/mojoman

---

### Post by royrules22 on 2007-04-21
Ok I installed gsynaptics, and it gave me this error:

""GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I followed the instruction in the second thread you linked to:

> **Carlos Santiago said:**
> Yes you must do it. 
To edit it, type: 
sudo gedit /etc/X11/xorg.conf

then just add 
Option 'SHMConfig' 'true' 
inside the section synaptics. 


However my xorg.conf doesn't have a synaptic section! What to do?

---

### Post by royrules22 on 2007-04-22
> **royrules22 said:**
> bump

..

---

### Post by 5-HT on 2007-04-22
[quote=royrules22] bump [/quote]The section itself should be 'InputDevice' (one of many). Do you have anything similar in your xorg.conf? Also, do you know if it is a Synaptics touchpad?

```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    .....
```

---

### Post by royrules22 on 2007-04-22
```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

```

I have a WACOM tablet I use and a Bluetooth mouse FYI.

How do I find out if my touchpad really is Synaptics?

---

### Post by mojoman on 2007-04-22
I did an ```
apt-cache search touchpad
``` abd the only driver it came up with is the synaptics driver. I'm not sure there are other drivers but I may very well be wrong here. Maybe some else can give some info on this?

Anyway, this is how an autogenerated section of a xorg.conf used for a toshiba laptop running on Debian etch looks like (this is how it looked before I started to tweak it, it was *really* slow on etch)
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

You could try adding this section, together with the SMHConfig option as well. If it works, well, you can start adding the options I recommended earlier on and see if that solves the problem. If not, it's easy enough to remove. But I find it strange that you don't have any section referring to your touchpad. Is your current xorg.conf autogenerated?

/mojoman

---

### Post by Rodtwister on 2007-05-16
I had the very same problem you have posted here (no synaptis Input Dev Section) I luckily solved it last night. I removed "xserver-xorg-input-synaptics" using Adept then I installed it (xserver-xorg............) again with Adept from the same Ubuntu 6.06 CD. It even told me there was another exact copy in another sub channel (whatever that means) After install was done I had the missing Section in "xorg.conf" Then I could do the things stated in this thread and other places. Problem solved. Maybe I can use Linux now. Well still have laptop winmodem problem, we'll see.

---

