---
title: "Logitech VX Nano"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by atlas95 on 2007-11-16
I'm waiting for my new logitech vx nano, but I havn't find yet a good howto for get working all the mouse buttons and set it (tweak) correctly.
Could you help me please?
Best Regards

---

### Post by -Phi- on 2007-11-18
I just got a VX Nano for my birthday (\\:D/) and now have the forward/backward buttons and side to side wheel working with btnx (see thread: [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)). I did have a problem some others had with Forward still registering as right click, but there's a fix for that on [page 6]("http://ubuntuforums.org/showthread.php?t=455656&page=6") if you get it too. I haven't messed with the Find button and left it mapped to middle mouse since the wheel doesn't have a click function.

Cheers!

- Phi

---

### Post by atlas95 on 2007-11-19
Hello,
I should receive it tomorrow :)
Thanks for you reply, but I have a favour yet :)
Could you make a little howto for resume all this threads? I'm french and I don't understand all sometimes...
Please just past the files I must add/edit and the package I must install...

Best Regards.:KS

edit: I have it, but i don't know what i must set in btnx-config after the button wizard...could you help me yet?
Thanks :)

---

### Post by atlas95 on 2007-11-19
Ho I have find how it works , I have just a problem, the "back" key on the mouse (the key front of the mouse) display the right clic popup even the action i have set with btnx work.
How to disable this double right clic?
(this is the same problem of you but i don't understand what i must do for change this :p)
Thanks

---

### Post by -Phi- on 2007-11-19
Glad it works! Here is what I did to solve the popup:

Open the file /etc/X11/xorg.conf as root
```
gksudo gedit /etc/X11/xorg.conf
```
You might want to save a backup of the unedited xorg.conf at this point just in case you accidentally change the wrong thing. Next find the section about your mouse. Mine looked like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
Change the Protocol line to "auto" from whatever it is, and make sure the driver is "mouse" (mine already was), so it looks something like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
Save, close, and reboot. That's it!

- Phi

---

### Post by atlas95 on 2007-11-20
Thanks you very much !
This is working!

---

### Post by warthogism on 2008-04-11
while the above suggestion worked to prevent my "up" button from emulating the right click, the right tilt now has assumed that role....

I cant seem to map some of the extra buttons.  I got the "zoom" button working as the middle mouse. and the "up" working as forward.  I mapped the down as back, but it doesn't work.  I mapped it in the same manner as i did the up/forward (key-right with leftAlt as the mod). that works.  and as stated above, the right tilt is now a right click even i mapped as key_right.  

Any help?

EDIT:  I'm an idiot.  I got all the buttons working now.  I just had to restart the btnx config a couple of times.  The problem for me was, some of the buttons mapped without a need for restart.  So I didn't think it was necessary.  Then, I even actually restarted the whole system a couple of times with no success.  it turns out, though, that if you just hit the "restart btnx" button under the configurations tab, everything works.  DUH.

---

