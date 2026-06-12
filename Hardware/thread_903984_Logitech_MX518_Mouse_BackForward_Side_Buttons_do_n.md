---
title: "Logitech MX518 Mouse Back/Forward Side Buttons do not work~"
date: 2008-08-28
forum: Hardware
---

### Post by _Atreides_ on 2008-08-28
I own a Logitech MX518 mouse, and the side thumb buttons do not seem to work in nautilus. They work fine in firefox going back and forward however. Any help to restore functionalities to the side mouse buttons so I could use them outside of firefox would be greatly appreciated! Thanks! :KS

---

### Post by _Atreides_ on 2008-08-28
Shameless bump in the name of all logitech users!

---

### Post by _Atreides_ on 2008-08-29
Well from the lack of responses, I am guessing there is no way to do this. However is there a version of logitech setpoint for linux?

---

### Post by _Atreides_ on 2008-08-29
After failing at googlefu, most of the guides I have found involve editing the X11.confg file. If it helps anyone get on track this is my respective portion of that file:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

---

### Post by nicedude on 2008-08-29
I must have a blacker googlfu belt :-)

Here is a xorg.conf for a MX500 but the creator stated it should work for most MX logitech mice, if nothing else it looks like a good start for you and you could always tweak it a bit if need be. You should check how your mouses buttons are setup compared to the MX500 and see if anything needs to be changed.


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800" #optional
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

Hope that works for you I felt compelled to try and help since you had been asking for a day without any replies.

Goodluck

---

### Post by scalywag66 on 2008-08-29
I have kind of a similiar problem with trying to find the folder/app so that I can map the side keys on my MX1000.

And when trying to map them in ingame menus, instead being mapped as MOUSE BUTTON 4, 5, 6, etc., whichever button I try to map comes up as TAB CONTROL, which is weird

---

### Post by nicedude on 2008-08-29
Heres a link for you scallywag but you don't need any extra programs to do this you just need to modify the mouse settings in your xorg.conf file located in /etc/X11/xorg.conf . Be careful to backup your xorg.conf file before modding it in case anything gets messed up since xorg.conf is pretty important if you want your system to work :-)

[http://adventuresinswitching.blogspot.com/2008/04/logitech-mx1000-mouse-on-ubuntu-804.html](http://adventuresinswitching.blogspot.com/2008/04/logitech-mx1000-mouse-on-ubuntu-804.html)


Hope that helps you

---

### Post by _Atreides_ on 2008-08-29
> **nicedude said:**
> I must have a blacker googlfu belt :-)

Here is a xorg.conf for a MX500 but the creator stated it should work for most MX logitech mice, if nothing else it looks like a good start for you and you could always tweak it a bit if need be. You should check how your mouses buttons are setup compared to the MX500 and see if anything needs to be changed.


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800" #optional
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

Hope that works for you I felt compelled to try and help since you had been asking for a day without any replies.

Goodluck


Yeah I tried tweaking around in the config file and still no luck (yes i restarted x) :(. I think it has more to do with Nautilus than the mouse now, considering the back buttons do work in firefox. Btw the MX500 looks exactly like the MX518. Thanks for the help guys hopefully the problem will just get patched up sometime soon. Do you know where I would go to file this bug/complaint/whatever you would call it?

---

### Post by prashime on 2008-09-25
Look here.....  [http://www.hidpoint.com](http://www.hidpoint.com)
Some 3rd party drivers and application is available. Looks like this might be the solution....

---

