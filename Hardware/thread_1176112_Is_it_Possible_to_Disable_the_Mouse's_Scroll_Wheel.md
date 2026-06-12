---
title: "Is it Possible to Disable the Mouse's Scroll Wheel?"
date: 2009-06-02
forum: Hardware
---

### Post by Blue Dolphins on 2009-06-02
[LEFT]The wheel on my mouse is broken and acts on it's own accord, can I disable the wheel so that I can continue using the mouse instead of the touchpad on the laptop?  I'm running Xubuntu 8.10.[/LEFT]

---

### Post by tgalati4 on 2009-06-02
Piece of electrical tape.

Comment out the appropriate lines in /etc/X11/xorg.conf

---

### Post by Blue Dolphins on 2009-06-02
There's nothing pertaining to the mouse in that  xorg.conf file to be commented out.

---

### Post by kerry_s on 2009-06-02
> **Blue Dolphins said:**
> [LEFT]The wheel on my mouse is broken and acts on it's own accord, can I disable the wheel so that I can continue using the mouse instead of the touchpad on the laptop?  I'm running Xubuntu 8.10.[/LEFT]

you shouldn't keep using it, it's probably reaping havoc sending weird signals to the kernel, maybe even filling your log files up with errors, is your disk running low on space, might want to check. :lolflag:

just wait till you can get a new 1.

---

### Post by tgalati4 on 2009-06-02
The newer xorg.conf files have nothing in them.  So you are correct.

Try adding:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
#        Option          "ZAxisMapping"          "4 5"
#        Option          "Emulate3Buttons"       "true"
EndSection

---------------------

See if that helps.

---

### Post by Blue Dolphins on 2009-06-02
> **kerry_s said:**
> you shouldn't keep using it, it's probably reaping havoc sending weird signals to the kernel, maybe even filling your log files up with errors, is your disk running low on space, might want to check. :lolflag:

just wait till you can get a new 1.
You can't be serious, what else can a mouse do besides sending mesages to move, click, or scroll?  That just seems illogical.

> **tgalati4 said:**
> The newer xorg.conf files have nothing in them.  So you are correct.

Try adding:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
#        Option          "ZAxisMapping"          "4 5"
#        Option          "Emulate3Buttons"       "true"
EndSection

---------------------

See if that helps.
I tried that, and it didn't change anything, I'm still getting erratic scrolling.

---

### Post by tgalati4 on 2009-06-03
Did you take the ball out and clean it?  Or is it optical.  Either way, some dust inside can cause erratic behavior.  Also, worn out wire where it comes out of the mouse can cause shorts which can harm your motherboard.  Better to replace it than to burn out some circuitry in your computer.

---

