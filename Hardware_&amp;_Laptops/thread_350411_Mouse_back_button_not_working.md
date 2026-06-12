---
title: "Mouse back button not working"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by PlancksCnst on 2007-01-31
I have  a Logitech MouseMan Wheel.  It is a wireless mouse with a left, right, middle wheel, and side buttons that connects to the PS/2 port.  I have not been able to get the back button (button 6) to work.  I use xev to check for the working buttons.

This is what my xorg.conf file says so far.
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Dev Phys" "isa0060/serio1/input0"
    Option         "Device" "/douseev/input/mice"
    Option         "Protocol" "IMPS/2"
    Option         "Buttons" "6"
    Option         "ZAxisMapping" "4 5"
EndSection

I have tried "MouseManPlusPS/2" (per the instructions [here]("http://www.xfree.org/4.3.0/mouse6.html#35")) for the Protocol option.  This makes the scroll wheel (buttons 2, 4, 5) not work as well as the side button still not working.  I have also tried  PS/2, IMPS/2, ExplorerPS/2, and Auto.  None of them work completely.  I have tried without the Buttons option and without the Dev Phys option.  They don't seem to make a difference.

Any suggestions?

---

### Post by tweedledee on 2007-01-31
If you can't get it to work automatically, you'll need to do a little manual work, but probably not much.  Look here: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).

---

### Post by PlancksCnst on 2007-02-04
I've already done what is relevant in that link.  Most of it is about mapping the button the the back event in the browser, but imwheel and similar progs won't even be able to see the button event (I know this because xev doesn't see it).

---

