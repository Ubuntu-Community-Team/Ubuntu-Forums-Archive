---
title: "GSynaptics Doens't Work"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by nadav2605 on 2007-04-03
I installed GSynaptics from synaptic package manager and when i try to start it it gives me the following error:
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

My computer is a dell inspiron E1405/640m and i'm running linux mint 2.2

Thanks!

---

### Post by mikewhatever on 2007-04-03
Just do what the error tells you to.
> sudo gedit /etc/X11/xorg.conf
the synaptic section should look like this
> Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
[COLOR="Blue"]    Option         "SHMConfig" "true"[/COLOR]
EndSection


---

### Post by nadav2605 on 2007-04-03
> **mikewhatever said:**
> Just do what the error tells you to.

the synaptic section should look like this

i tried, i don't have that section in my xorg.conf
what should i do?

---

### Post by BUGabundo on 2007-04-04
you must add:
 Option "SHMConfig" "true"

---

