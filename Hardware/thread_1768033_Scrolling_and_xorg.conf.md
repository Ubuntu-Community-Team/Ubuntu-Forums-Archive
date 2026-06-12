---
title: "Scrolling and xorg.conf"
date: 2011-05-26
forum: Hardware
---

### Post by specialalaa on 2011-05-26
Hello. This is how I'm running Ubuntu: **Ubuntu 11.04** installed on a virtual machine using **VMWare Workstation v7.0.1**.

***My Problem:***
I cannot scroll using the touchpad (on my Sony VAIO E series)

***What I've tried:***
Edit some files, rename some files, move some files, log in to virtual terminals, some reboots, set my laptop on fire, putting out the fire; but nothing worked. Here's thoroughly what I did:
[LIST]
[*]After some searching, I found out that it has something to do with the xorg.conf. I had to edit in the following:
```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
EndSection
```
[*]So I did "***sudo gedit /etc/X11/xorg.conf***", and it opened up a blank file. I navigated to the folder /etc/X11/ to find out that xorg.conf does not exist there
[*]After some more searching, I had to "***sudo Xorg -configure***" to generate a new xorg.conf (after stopping gdm)
[*]So I "Ctrl+Alt+F2" and logged into the virtual terminal; did "***stop gdm***"; did "***sudo Xorg -configure***", it gave me some errors but in the end it generted the xorg.conf.new file somewhere.
[*]So I "***start gdm***"; open up the new xorg file (it had a lot of sections; I have it if someone wants to see it), change the section I have to change; renamed and copied the file to /etc/X11/
[*]Restart my virtual machine and voila!, Ubuntu does not boot up =D (stuck at the "Ubuntu" with 5 dots screen).
[*]After some reboots, I managed to log into a virtual terminal; did "***stop gdm***"; renamed the xorg.conf file to something else; "***start gdm***" and I'm back into GNOME, safe and sound. 
[/LIST]
So...can someone help me out? I have no problem in reinstalling Ubuntu again and starting from scratch if that's what it takes.

If it's worth anything, I'm using an ATI Mobility Radeon HD 5650 graphics card.

---

