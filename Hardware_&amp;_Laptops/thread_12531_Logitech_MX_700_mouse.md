---
title: "Logitech MX 700 mouse"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by Tiiba on 2005-01-25
I know it works in Redhat, Mandrake, and Mepis. So why not Ubuntu? Is there any way to set it up?

---

### Post by TravisNewman on 2005-01-25
See the HOWTO:Thumb Buttons in the FAQ/HOWTO forum. :)

---

### Post by Tiiba on 2005-01-25
I don't need thumb buttons. It doesn't work at all...

---

### Post by martyr on 2005-01-25
I've been using an MX500 and an MX510 on Ubuntu without any problems. Apart from the thumb buttons, it worked out of the box.

As the MX500 and the MX700 share the same architecture, I suggest checking that your mouse is correctly connected to the receiver and that there is no other wireless device using the same frequency around.

---

### Post by Tiiba on 2005-01-25
It's connected. I'm using it now from Windows. Ubuntu is the only system that doesn't see it.

---

### Post by martyr on 2005-01-26
When you go to Computer -> System Configuration -> Device Manager, does your mouse show up in the list?

---

### Post by TravisNewman on 2005-01-26
D'oh! Sorry bout that, I completely misunderstood.

---

### Post by Tiiba on 2005-01-26
[QUOTE=martyr]When you go to Computer -> System Configuration -> Device Manager, does your mouse show up in the list?[/QUOTE]
It shows a PS/2 compatible mouse and an HIS-compliant mouse. What's HIS?

I have another mouse, which works with Ubuntu, despite the fact that its make is not indicated anywhere on it (model is HTM-92W, though), and it has no FCC ID that I could search for. (Is that legal?) It plugs into a PS/2 port. MX700 uses USB.

---

### Post by martyr on 2005-01-26
Did you modify and/or recompile your kernel?

Is /etc/X11/XF86Config-4 correctly set up for an USB mouse? (Does it contain an InputDevice Section that describes your mouse and is that mouse actually selected, right at the bottom of the file, in the ServerLayout section?)

---

### Post by Tiiba on 2005-01-26
[QUOTE=martyr]Did you modify and/or recompile your kernel?

Is /etc/X11/XF86Config-4 correctly set up for an USB mouse? (Does it contain an InputDevice Section that describes your mouse and is that mouse actually selected, right at the bottom of the file, in the ServerLayout section?)[/QUOTE]
I looked at the config and saw no reference to a USB mouse. I tried to copy the corresponding section from the Mepis LiveCD:

Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "ZAxisMapping" "4 5"
  Option "Buttons" "5"
EndSection

Section "ServerLayout"
  InputDevice "USB Mouse" "CorePointer"
 # Other stuff
EndSection

X gave me a screen that looked unsettlingly like the  BSOD. Why? And what is "ExplorerPS/2" doing in a USB mouse? (Like I said, this works fine in Mepis)

---

### Post by martyr on 2005-01-27
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

[...]

Section "ServerLayout"
        [...]
        InputDevice     "Configured Mouse"
EndSection
``` 

This is an excerpt from XF86Config-4, using an MX510. Generally, it should work for you.

The ExplorerPS/2 Protocol is for Microsoft Explorer mice.

---

### Post by Tiiba on 2005-01-27
That proved useless. I tried to change the protocol to usb and the device to /dev/input/mouse0,, but to no avail.

---

### Post by butt on 2005-02-09
[QUOTE=Tiiba]I know it works in Redhat, Mandrake, and Mepis. So why not Ubuntu? Is there any way to set it up?[/QUOTE]
 your not the only one having this problem, i have been trying to make it a point that lots of people are having trouble and not getting any resolution to this problem, there seems ot be a lack of support for this issue.

---

### Post by globalspace on 2005-03-05
I'm using Logitech MX 700 without problems ... it is attached to USB and it works :)

this is my /etc/X11/XF86Config-4

> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
 

i'm studying to do works the lateral buttons  :sad:

---

### Post by cmsj on 2005-08-10
[QUOTE=][/QUOTE]
 [http://ubuntuforums.org/showthread.php?p=295653#post295653](http://ubuntuforums.org/showthread.php?p=295653#post295653) may help

---

