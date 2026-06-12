---
title: "External PS/2 mouse and Viking CF don't work"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by theboatashore on 2005-05-11
Hi

I'm a complete newbie who switched when my Windows machine crashed.  My external PS/2 mouse and Viking compact flash don't work, otherwise I love the new OS.  I'm running Ubuntu on a Compaq Presario 900 with a Synaptic touchpad, which works fine.  When I look at /etc/X11/xorg.conf (I'm not sure if this is the right place) I get the following message:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option	"CorePointer"
	Option	"Device"		"/dev/input/mice"
	Option	"Protocol"		"ImPS/2"
	Option	"Emulate3Buttons"	"true"
	Option	"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

This seems to indicate that that both are configured, but the external mouse still doesn't work.

As far as the compact flash is concerned, it's a Viking CF card that I plug it into a Viking PCMCIA adapter.  I know that whatever controls the PCMCIA slot works because my wireless network card (Netgear) works fine.  Is Viking supported?

I've searched everywhere I can think of and can't resolve these two issues.  Please help.

Thanks,
Michael

---

### Post by cowbud on 2005-05-11
I had the same problem and the issue was the mouse module wasn't being loaded. 

try:

**sudo modprobe psmouse **

and look at dmesg by typing dmesg as any user, and see if it mentions a PS2 mouse. 

If it does /dev/psaux should now be where your PS2 mouse can be accessed. 

if not try installing mdetect and run it with sudo. This should say if your mouse is detected or not.

---

### Post by theboatashore on 2005-05-11
Hey

After running **sudo modprobe psmouse** and then **dmesg**, I get the following text:

mice: PS/2 mouse device common for all mice
Synaptics Touchpad, model: 1
 Firmware: 5.9
 180 degree mounted touchpad
 Sensor: 29
 new absolute packet format
 Touchpad has extended capability bits
 -> 4 multi-buttons, i.e. besides standard buttons
 -> multifinger detection
 -> palm detection
input: SynPS/2 Synaptics TouchPad on isa0060/serio1

When I run **sudo mdetect**, I get the following:

/dev/psaux
intellimouse

When I look in*/dev/psaux*, the file's icon is red with a white cross in the middle and when I try to view/edit it, I get the following message:

Can't disply /dev/psaux

I'm not sure what all this means, except that my mouse is still not working.

---

### Post by GordonInc on 2005-05-27
Maybe try replace  Option "Device" "/dev/input/mice"
with Option "Device" "/dev/psaux"  ?

---

### Post by theboatashore on 2005-06-01
Sorry, still no luck.  Any other ideas?

---

### Post by Jussi on 2005-07-05
Hello,

I am having the same problem with my Compaq Evo N1020v (PS/2 mouse does not work but touchpad does). Even the xorg.conf was the very same! Now I've been trying to search help in forums and everywhere but I still cannot get it working.

All help is appreciated,
 -Jussi

---

### Post by tarvas on 2005-07-20
[QUOTE=Jussi]Hello,

I am having the same problem with my Compaq Evo N1020v (PS/2 mouse does not work but touchpad does). Even the xorg.conf was the very same! Now I've been trying to search help in forums and everywhere but I still cannot get it working.

All help is appreciated,
 -Jussi[/QUOTE]

Same computer, same mouse (optical, Genius), same problem.
If nobody will help, i'll uninstall Ubuntu. :@

---

