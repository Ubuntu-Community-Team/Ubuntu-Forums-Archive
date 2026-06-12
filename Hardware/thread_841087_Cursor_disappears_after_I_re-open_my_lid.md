---
title: "Cursor disappears after I re-open my lid"
date: 2008-06-26
forum: Hardware
---

### Post by Steve90210 on 2008-06-26
Sometimes after I've closed my laptop lid for a while and re-open it, my cursor disappears. They only way I can tell where it is is if I scroll all the way to the top of the screen and then run it over the date icon, which will then become highlighted. I then have to restart the computer. Logging off and then logging in again does not solve the problem. 

Has anyone else experienced the cursor disappearing problem and fixed it? I'd rather not have it disappear on me. lol

As for my 'Power Management' settings, they are:



> *On AC Power:*

Put computer to sleep when inactive for: Never

When laptop lid is closed: Blank screen

Put display to sleep when inactive for: Never


*On Battery Power*

When laptop lid is closed: Blank screen

When battery power is critically low: Shutdown

Put display to sleep when inactive for: Never

Reduce backlight brightness: check

Dim display when idle: check



---

### Post by Steve90210 on 2008-06-26
The laptop is a HP dv9000 aka dv9420ca, if it helps.

---

### Post by Steve90210 on 2008-06-28
I know I'm not the only one with this problem...

---

### Post by Steve90210 on 2008-07-03
How do I troubleshoot this?

---

### Post by sisco311 on 2008-07-03
Edit your xorg.conf:
```
gksu gedit /etc/X11/xorg.conf
```and add this line
> **Option "HWCursor"  "False"**
to the Device section

Example:
> ...
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "driver"
    **Option "HWCursor"  "False"**
EndSection
...

EDIT: Save the file and press Ctrl+Alt+Backspace to restart the x server

---

### Post by specialk1st on 2010-07-13
You can use this as a workaround to get back the missing cursor after opening your laptop lid ...

Try switching desktops via:
Ctrl+Alt+LeftArrow OR Ctrl+Alt+RightArrow

It is a reported bug.

Resource:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058)

---

