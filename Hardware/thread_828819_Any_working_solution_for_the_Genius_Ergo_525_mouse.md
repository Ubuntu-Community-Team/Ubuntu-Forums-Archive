---
title: "Any working solution for the Genius Ergo 525 mouse?"
date: 2008-06-14
forum: Hardware
---

### Post by 0x656b694d on 2008-06-14
Hi,

Do anybody have working all 11 buttons of Ergo 525 mouse?

The following options make left-side buttons controls the volume. I tried to use other buttons in Compiz, but with no success.
xev shows some events on up and down buttons (8 and 9?).
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "11"
EndSection

```

I would like to use "3D"-wheel (button 6,7?) to switch windows, for instance.

Thanks!
-Mike.

---

### Post by forejtv on 2008-08-28
Hello, I have the same problem as you and I don't want to start new thread, so I only post some more details here. Hopefully, someone will reply.

I have a Genius Ergo 525 mouse, which I'm trying to get to work. The problem is that after the instalation, the system does not detect moving the whell left/right, but only scrolling it up/down (at least xev gives me no event and cat /dev/input/mice outputs nothing when I move the whell left or right).  In /etc/X11/xorg.conf, I have the following settings

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Buttons" "11"
EndSection
```


However, if I change xorg.conf to the following

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver "evdev"
        Option "CorePointer"
        Option "Device" "/dev/input/event2"
        Option "Buttons" "11"
EndSection
```

the moving of the wheel is correctly recognized as button 7 (left) and 6 (right). The problem is that with this configuration, the cursor only moves up and down, i.e. if I move the mouse right, the cursor does not move (actually, it does, but only a bit up and down as I cannot move the mouse precisely to the right), and if I move it left and down, it only moves down. Also, the keyboard buttons behave strangely with this settings (e.g. when I press delete, a window "save screenshot" pops up, when I pres "insert", "/" is typed).

cat /proc/bus/input/devices gives me the following output (I only post sections for keyboard and mouse here)

```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=400402002000 3803078f810d001 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0458 Product=005c Version=0110
N: Name="Genius Ergo Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2
B: EV=2001f
B: KEY=37fff00ac3027 bf00444400000000 70001 c040a37c000 267bfad9415fed 8e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10
B: LED=80
```

So, could anybody help us? Thanks in advance.

---

### Post by marcordenis on 2008-09-22
I'll also join in this thread, as  I have just recently bought a Genius Ergo 555. I think it is not far too different from the 525. I got btnx, as was said somewhere, but if I click with any other button than my left, right, and scroll wheel, it is not recognized. Any help would be appreciated.

---

### Post by 0x656b694d on 2008-09-23
Hey! Guess what?!
Without any special tunings i got all buttons working in 8.10: left/right wheel swaying moves back/forward in Opera browser, left-side buttons switch the sound volume.
I also see that the focus rectangle blinks on a tab header when i click that small buttons around the wheel.

So, the last problem is... how to programm the behavior?

Linux ubu 2.6.27-4-generic #1 SMP Mon Sep 22 04:40:44 UTC 2008 i686 GNU/Linux

DISTRIB_RELEASE=8.10

I've deleted the xorg.conf and use the automatically generated one.

-Mike

---

### Post by nanux on 2008-12-22
Hallo,

I am not sure what I did wrong, but I can't get mouse to work...

My xorg.conf:

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

I think, it is the default that come with ubuntu 8.10.

Can you paste your xorg.conf? Or did you anything in addition to get the mouse to work?

Thank you

---

### Post by dbius on 2009-01-11
> **0x656b694d said:**
> Hey! Guess what?!
Without any special tunings i got all buttons working in 8.10: left/right wheel swaying moves back/forward in Opera browser, left-side buttons switch the sound volume.
I also see that the focus rectangle blinks on a tab header when i click that small buttons around the wheel.

So, the last problem is... how to programm the behavior?

Linux ubu 2.6.27-4-generic #1 SMP Mon Sep 22 04:40:44 UTC 2008 i686 GNU/Linux

DISTRIB_RELEASE=8.10

I've deleted the xorg.conf and use the automatically generated one.

-Mike

Thx. I'll give it a try.

---

