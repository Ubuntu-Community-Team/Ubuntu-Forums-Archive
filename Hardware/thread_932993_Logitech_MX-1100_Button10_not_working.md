---
title: "Logitech MX-1100 Button10 not working"
date: 2008-09-29
forum: Hardware
---

### Post by steampoweredlawngnome on 2008-09-29
Hello,

I just purchased a Logitech MX-1100 this weekend, and I'm having trouble getting anything but xev to recognize Button10. I have buttons 1-9 recognized, showing up in CCSM, and mapped to functions, but Button10 is still more or less non-functional. 

CCSM lists Button1 - Button9, and when I try to force Button10 through gconf-editor, it just drops the 0 and treats it as Button1.

xev recognizes Button10 as a unique button, so I'm not at all sure what's wrong at this point. Here is the relevant portion of my xorg.conf;

Section "InputDevice"

#   generated from default
#   Option         "Emulate3Buttons" "no"
    Identifier     "MX-1100"
    Driver         "evdev"  #was "mouse"
    Option         "Protocol" "evdev" #was "auto"
    Option         "Phys" "usb-*/input1"
    Option         "Device" "/dev/input/event1"
    Option         "Buttons" "10"
    Option         "CorePointer"
#   Option         "ZAxisMapping" "4 5"
    Option         "ZAxisMapping" "4 5 7 6"
#   Option         "ZAxisMapping" "4 5 7 6 10"
#   Option         "HWHEELRelativeAxisButtons" "6 7"
EndSection

Commented out lines are those that I already tried with no success.

Anyone have any ideas? I've followed all the threads I can find for the MX-1000 and MX-Revolution, but they do not seem to address the hidden thumb button, Button10.

My goal is to make Button10 function as the move window button, rather than <Alt>Button1.

Thanks in advance!

---

### Post by quackeroni_pizza on 2009-04-17
I just got one myself and can confirm the same problem...  I haven't played with xev yet.... All we have to do is detect this button and map it to Alt+Tab for application switching?

Any updates on this problem??

---

### Post by killabee44 on 2009-05-05
I just got this mouse and am trying to get it to work as well. Please post any ideas. I will keep searching too.

---

### Post by steampoweredlawngnome on 2009-07-24
Haven't visited the site in a while, but figured I'd post the solution I eventually found for this problem.

Install BTNX. BTNX will recognize all of the buttons on the mouse and allow you to assign keyboard combinations, or keyboard/mouse button combinations to buttons.

In this case, you could assign Alt+Button1 to Button 10, or now that I'm using KDE, I set it to CTRL+F12 to bring up my Plasma dashboard.

---

### Post by ___Kevin___ on 2009-12-06
Hi, had the same problem, here's an easy fix:

In CCSM click the edit-button next to the action you want to have on button 10. In the textfield, just type Button10 as the button name. Allthough CCSM doesn't allow to select Button10 from the drop-down list, you can still use it when simply typing it.

---

### Post by cheflo on 2010-08-17
Bumping this one. I can get button 10 to work but neither xev nor BTNX register any input from the two buttons used to adjust the dpi of the mouse. They work perfectly for adjusting the dpi, but I would like to bind them to something else, like a custom command. Has anyone had any luck with this?

---

