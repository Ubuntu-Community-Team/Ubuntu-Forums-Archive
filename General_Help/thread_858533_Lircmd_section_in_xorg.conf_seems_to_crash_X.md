---
title: "Lircmd section in xorg.conf seems to crash X"
date: 2008-07-13
forum: General Help
---

### Post by jdkoola on 2008-07-13
I added the standard section to xorg.conf

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

And I added 

InputDevice "LIRC-Mouse"

to the ServerLayout

but this seems to make X crash and dmesg shows "segfault" when X attempts to startup, and I get the dialog box saying that my videocard and monitor are not recognized.

I'm running Mythbuntu 8.04 and using a Windows MCE remote.  I have my regular mouse also plugged in, and my mouse also has an entry in the xorg.conf.  I don't know if that's causing problems.

Any help is appreciated.

---

### Post by don_engtech on 2008-07-27
Same thing happened to me. Fought with it for days.
Seems related to LIRC starting up after gdm.  Followed the advice on this thread and my remote works perfectly now.

Check out this thread:
[http://ubuntuforums.org/archive/index.php/t-425660.html](http://ubuntuforums.org/archive/index.php/t-425660.html)

Hope that helps,
Don

---

