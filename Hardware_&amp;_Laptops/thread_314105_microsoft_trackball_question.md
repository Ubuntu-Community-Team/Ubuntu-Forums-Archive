---
title: "microsoft trackball question"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by gt3 on 2006-12-07
I have a "microsoft trackball optical 1.0 ps2/usb compatible Product ID: 52240-576" and it has extra buttons that act like browser 'back' and 'forward' buttons in web browsers but by default it's not working in Ubuntu. Is there a way to get it to work?

When I first boot up ubuntu it says:
[17179570.748000] mice: PS/2 mouse device common for all mice
[17179596.868000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2

---

### Post by Kaladar on 2007-04-23
I have this mouse as well. It works more or less, other than the two extra 'back/forward' buttons. My back button does nothing and the forward button just does a right-click.

my mouse section of Xorg.conf is like so:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Maybe that will stop your errors.

Has anyone been able to make this mouse work like it does in Windows?

---

### Post by morequende on 2007-06-01
Same thing here... has anyone made it to work?:p

---

### Post by pablo66 on 2007-06-02
I have the identical mouse too. How do we write a driver for it?

---

### Post by Mikebert on 2007-12-02
I know this topic is years old, but I still get referred to it in google, so here's how to fix the problem.  I'm using Linux Mint 4.0, but I have every faith this helps in other distros.  I have tried every other solution listed at linuxquestions or the Ubuntu forums with no luck.  

```

1) At some point, I installed imwheel.  
I honestly don't know if it makes a difference after all the tricks and hacks I tried, but .. .eh, do it.

sudo apt-get install imwheel

2) Whip out your sudo and edit your mouse section in /etc/X11/xorg.conf
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Buttons"       "7"
        Option          "ZAxisMapping"  "4 5"
#       Option          "Emulate3Buttons"       "false"
EndSection

3) You'll have to make sure this is executed every login.  
An easy way to make is go to Prefs > Sessions and Add this as a Startup Program.

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"

```

Viola.

---

### Post by mastergunner on 2007-12-17
,,,

---

