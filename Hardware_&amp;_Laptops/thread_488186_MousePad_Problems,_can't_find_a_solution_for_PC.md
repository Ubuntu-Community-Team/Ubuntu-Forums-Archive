---
title: "MousePad Problems, can't find a solution for PC"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by Prosis on 2007-06-29
I followed a tutorial on the french Ubuntu website ([http://doc.ubuntu-fr.org/materiel/touchpad#problemes_de_contact_de_paume](http://doc.ubuntu-fr.org/materiel/touchpad#problemes_de_contact_de_paume)) to deactivate the mousepad whilst typing.  After restarting X and launching the TouchPad application, I get this error:

```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

So I looked around and found some help and added this to my xorg.conf:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```

so that I could use the command:

```
syndaemon -d -t -k -i 2
```

and I got 

```
Can't access shared memory area. SHMConfig disabled?
```

SO now I don't know what to do anymore and all I can find is help for Macs and I'm on PC.  

Did anyone have this problem and knows how to solve it?

Thanks

---

### Post by Prosis on 2007-06-29
Ok nevermind, I needed to add this

Section "ServerLayout"
        [...]
        InputDevice     "Synaptics Touchpad"    "AlwaysCore"
EndSection

Works fine now :D

---

