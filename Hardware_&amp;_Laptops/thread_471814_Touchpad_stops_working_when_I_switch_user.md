---
title: "Touchpad stops working when I switch user"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Smiley-Man on 2007-06-12
Encountered a strange problem and have searched but have not found anything similar.

When I switch user, The user I switch to can not use the touch pad and it stays locked up until I switch back to the other user.

Using Gsynaptics and its a synaptics touchpad.

Toshiba A100 Laptop.

Thanks.

---

### Post by Smiley-Man on 2007-06-12
Anyone?

---

### Post by JPJ on 2007-06-16
I have the same problem with a Dell Inspiron E1705 with an nVidia display card.  If I find a solution, I'll try to respond here.

---

### Post by dbl76 on 2007-07-03
Does anyone have any more information on this problem?
I have the same issue with a Lifebook C1020 laptop with Synaptics touchpad... (under feisty)

Thanks

---

### Post by smalleraperture on 2007-07-07
I am having the same problem on my Acer laptop.  Looking forward to a solution.  In the meantime:

Make sure the touchpad is enabled.  There may be a button above the touchpad to toggle it, or, as on my laptop a keyboard combo using such as Fn+F7.

This didn't solve my problem, but it might work for some.

---

### Post by JPJ on 2007-07-10
Try locking the screen before switching user.  That seems to work on my E1705.

---

### Post by floke on 2007-07-10
Yes this is crap - what's the point of having a switch feature if you can't really switch? AFAIK you have to switch back and forth a few times to get the touchpad to 'stick', but then the sensitivity tends to be screwed.

---

### Post by mrund on 2007-07-10
I've got the same problem on a Dell Inspiron 6000. Didn't work in Edgy, doesn't work in Feisty. A plug-in mouse works, however.

---

### Post by Mud.Knee.Havoc on 2007-07-15
Same here.  When I want to switch users, I have to plug in my usb mouse because the touch pad won't recognize anything.  But if I have the usb mouse plugged in when switching users, it works fine.  It's something with the touch pad.

---

### Post by snifer on 2007-07-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/68370](https://bugs.launchpad.net/bugs/68370) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This bug has been reported at launchpad.

---

### Post by klato on 2007-07-24
I've had this exact problem since at least Edgy...

A total pain in the *** as I sometimes even have to reboot my machine just to get the touchpad to work again.  Kind of renders user switching completely useless.

---

### Post by dougalf on 2007-07-30
A quick and dirty fix is to move the buggy driver aside
```
cd /usr/lib/xorg/modules/input 
sudo mv synaptics_drv.so synaptics_drv.so.broken
```
and reboot.

However you may find that the touchpad becomes much less user friendly.

---

### Post by eel on 2007-08-14
dear smalleraperture
thanks for your help
discovering there was an on/off switch (fn F9) on my laptop made me feel both stupid and happy :)

---

### Post by Thingymebob on 2008-01-10
Had the same problem on my acer aspire 5100 and my aspire 1350, found that making the following changes to /etc/X11/xorg.conf solved it on both machines:
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	**Option	    "CorePointer"**
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	**Option	    "SendCoreEvents" "true"**
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "event3"
	Option	    "HorizScrollDelta" "0"
EndSection
```changed to
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	**Option	    "SendCoreEvents" "true"**   
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	**Option	    "CorePointer"**
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "event3"
	Option	    "HorizScrollDelta" "0"
EndSection
```

---

