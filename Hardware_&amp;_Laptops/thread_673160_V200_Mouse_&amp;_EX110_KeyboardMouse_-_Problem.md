---
title: "V200 Mouse &amp; EX110 Keyboard/Mouse - Problem"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by cmavr8 on 2008-01-20
Two Logitech USB transmitters/receivers = PROBLEM:

Hello,  I use a logitech usb keyboard (from EX110 keyboard+mouse COMBO) and a usb (separate receiver) logitech mouse (V200).


If I do dpkg-reconfigure xserver-xorg and just plug in both usb receivers, everything works except for the mouse roller tilt. I used a guide for fixing this (found in this forum) and I replace the default mouse part with this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Receiver"
EndSection
```

Now, I need to have the keyboard receiver plugged out for the mouse to work. The mouse works perfectly.

The problem is that both of the receivers have the name "Logitech USB Receiver" and that causes a problem when I use it to configure the mouse separately in xorg.conf...

Any ideas on how to rename one of the two? ("Logitech USB Receiver MOUSE")

I have the results of cat /proc/bus/input/devices:

With the V200 mouse plugged in:
```
I: Bus=0003 Vendor=046d Product=c510 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-7.1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse2 event3 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: LED=ff00
```


With the EX110 Keyboard+Mouse combo plugged in:

```

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/class/input/input16
U: Uniq=
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f


I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2/input1
S: Sysfs=/class/input/input17
U: Uniq=
H: Handlers=kbd mouse2 event4 
B: EV=f
B: KEY=7fff 42c332f bf084440 0 0 ff0001 1f84 8837cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

```

See? The same "Logitech USB Receiver" name. And even worse, the combo makes two entries, so if I plug both receivers in, I'll have THREE! No wonder why X doesn't boot...

Can I "rename" those entry names?

Thanks for reading.

---

### Post by jorwex on 2008-02-09
Did you ever find a solution to this problem? I have a MX1000 and was looking to get the EX110 just for the keyboard like you seem to be aiming for.

---

### Post by cmavr8 on 2008-02-09
No solution yet..

I just use the keyboard from the ex110 pack, and my separate wireless mouse, but without the wheel tilt buttons.

If you don't want the tilt wheel buttons, the configuration works out of box.

---

### Post by jorwex on 2008-02-09
BTW here's my xorg.conf section for my mouse:

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

mine doesnt say Logitech anywhere in the file. does yours only say that cuz of what you did to get the tilt working? 

i havent bothered fixing any of the problems with my mouse and ubuntu (no tilt, no side buttons, no quick up/down cruise control...or wahtever it's called).  i just got used to not using them. 

so will i not have a problem if i dont manually change the xorg for my mouse's extra features?

thanks and good luck!

---

