---
title: "Touchpad Issue"
date: 2008-11-01
forum: Hardware
---

### Post by shreyaspotnis on 2008-11-01
Hi,

I recently upgraded my dell 1525 laptop from gutsy to hardy. Everything seems to be working fine expect my touchpad. It works fine during the login screen, but as soon as I login it starts behaving in a weird way.
Whenever I touch the touchpad somewhere the cursor jumps to the respective position on the screen. It's not relative, as before. Like if I touch the top right section of the touchpad, the cursor will jump to the top right section of the screen.

I had installed gsynaptics in gutsy before and configured the xorg.conf file to enable SHMconfig

The xorg.conf part for the touchpad:
```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "MinSpeed" "0.6"
        Option      "MaxSpeed" "0.9"
        Option      "AccelFactor" "0.10"
        Option      "SHMConfig" "on"

```

Please Help!
Shreyas

---

### Post by eaidoido on 2008-11-01
tried reverting back to the default xorg.conf?

---

### Post by shreyaspotnis on 2008-11-01
Removing the SHMConfig line from the xorg.conf file did it. :) Who needs the graphical interface anyway. I hardly change the touchpad settings.

Thanks,
Shreyas.

---

### Post by Bronto on 2008-11-01
You can now use System -> Preferences -> Mouse -> Touchpad to change (some of) the settings.

---

