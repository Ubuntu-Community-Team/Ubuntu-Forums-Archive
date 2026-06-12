---
title: "Completely New to Ubuntu; Acer X223W install question."
date: 2008-12-04
forum: Hardware
---

### Post by mookauuu on 2008-12-04
hey, i'm completely new to ubuntu.

my brother and i recently got a new shuttle pc and installed ubuntu on it.

and was got the Acer X223W monitor.

the monitor works, but the screen resolution is all messed up.

i have absolutely no clue how to fix it.

the resolution is now at 800x600.

this is a 22" monitor, and i know it can do better then that.


sorry about being such a n00b about this, but i would appreciate any help.

thank you.

---

### Post by taurus on 2008-12-04
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X server with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to the GUI login screen and restart the X server with <Ctrl><Alt>Backspace.

Log in and see if you get a higher resolution now.

---

### Post by mookauuu on 2008-12-04
ok, did that.

and nothing has changed.:confused:

---

### Post by taurus on 2008-12-04
What kind of graphic card do you have?

You can try to boot into recovery mode from GRUB menu and pick the fix xserver option from the list and see if that does it.

---

### Post by mookauuu on 2008-12-04
i have no clue what kind of graphics card.

i actually dont even know if we got one?


i'll talk to my brother when he gets home and let you know.


thanks.

---

### Post by taurus on 2008-12-04
Run this command from a terminal and it will tell you exactly which graphic card you have in that machine.

```
lspci | grep VGA
```

---

### Post by mookauuu on 2008-12-04
shuttle@shuttle-desktop:~$ lspci | grep VGA
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7025 (rev a2)
shuttle@shuttle-desktop:~$ 


that is what came up.

---

### Post by taurus on 2008-12-04
It's an nVidia card.  Look in System -> Administration -> Hardware Drivers and see if your card is on the list.  And if it is, see if you can install (enable) a driver for it.

---

### Post by mookauuu on 2008-12-04
ok, it said downloading.

and finished.

now what do i do?

---

### Post by taurus on 2008-12-04
There is a blue icon on top panel telling you to reboot.

---

### Post by mookauuu on 2008-12-04
i restarted the computer and there is no difference.

i even went into system<preferences<screen resolution and there is no option to go any bigger then 800x600 :confused:

---

### Post by mookauuu on 2008-12-04
Wait!

I GOT IT!

thanks

---

### Post by Wolycan on 2009-09-06
im having the same problem and none of that is working for me, im stuck in 1024x768
on reboot, i see the "try to repair graphics problems" but nothing about xserver, any help?

---

### Post by Kilgore!!!! on 2009-09-17
The easiest way -- for me-- to change the resolution of the screen, was to change the "xorg.conf" file.  This is the file that can be used to place custom values for specific hardware.

1. Make sure that you back up your xorg.conf file with this command:
             **cp /etc/X11/xorg.conf   .**

2. Copy-- as root-- into your /etc/X11/xorg.conf file -- overwriting the "Monitor" (refresh rates now specified) and the "Screen"(screen size capability now specified) sections:


[B]
Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection    "Display"
        Depth    24
        Modes    "1680x1050" "1024x768"
    EndSubSection
    SubSection    "Display"
        Depth    32
        Modes    "1680x1050" "1024x768"
    EndSubSection
EndSection
[/B]
3.  Hit <ctrl> <alt><backspace> to hard restart your XServer.   Ta-Da!
4. You can define more sizes by adding sizes to the "Modes" sections. :)

---

