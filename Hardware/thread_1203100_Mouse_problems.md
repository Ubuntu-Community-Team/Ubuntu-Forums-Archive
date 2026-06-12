---
title: "Mouse problems"
date: 2009-07-02
forum: Hardware
---

### Post by Shadowrunner340 on 2009-07-02
Hi all, I'm having some real trouble with my mouse. For some reason, my scroll wheel has developed a mind of its own and has decided to commandeer anything that responds to the scroll wheel. It seems to be interrupting other mouse functions, as well, because I have a real hard time dragging anything.

Here's my xorg.conf mouse section:

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

---

### Post by Shadowrunner340 on 2009-07-03
Anybody?

---

