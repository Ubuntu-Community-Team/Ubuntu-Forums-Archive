---
title: "Synaptics is too sensitive"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by ZeXr0 on 2005-10-13
Is there a way to change the sensitivity of synaptics,
Because I can't almost move my mouse without doing a single click :S

btw : ubuntu is way too cool :)

---

### Post by simohell on 2005-10-13
You can change the settings from your xorg.conf file
with MaxTapTime. Setting it to "0" will disable tapping.
The default value 180 seems to me way too sensitive.

[INDENT]
[...]
Section "InputDevice"
 [INDENT]       Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        [COLOR="SeaGreen"]Option          "MaxTapTime"           "0"[/COLOR]
[/INDENT]EndSection
[...]
[/INDENT]

(the file xorg.conf should be in the directory /etc/X11 )

---

### Post by Corvillus on 2005-10-14
There is also a configuration utility called QSynaptics which lets you fine tune the touchpad settings within a GUI.

---

