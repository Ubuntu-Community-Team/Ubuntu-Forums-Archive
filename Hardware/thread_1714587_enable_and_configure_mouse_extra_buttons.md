---
title: "enable and configure mouse extra buttons"
date: 2011-03-25
forum: Hardware
---

### Post by krad23 on 2011-03-25
hey guys. i'm an absolute newbie here, so bear with me..
i have a logitech m705 mouse and i want it configured like i have it in win:

for back/forward (now configured to side buttons) i want the middle button left-right
the side buttons i want to minimize and close windows
and the thumb button (not working at all right now) i want it for Control+W (close tab)

from what i've read it's something i have to do in xorg.conf, but i don't want to screw things up, so here's the present configuration

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

 
any help? :D

---

### Post by krad23 on 2011-03-26
bump

---

### Post by krad23 on 2011-03-27
no one?

---

### Post by krad23 on 2011-03-28
i tried something i found in xorg.conf, but then my ubuntu wouldn't boot.. :))

---

