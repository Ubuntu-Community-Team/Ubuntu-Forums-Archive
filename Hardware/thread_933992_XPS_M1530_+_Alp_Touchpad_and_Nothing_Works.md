---
title: "XPS M1530 + Alp Touchpad and Nothing Works"
date: 2008-09-30
forum: Hardware
---

### Post by walkingthecow on 2008-09-30
Hi All,

I have a Dell XPS M1530 with a Dell Alp Touchpad. So far, everything on the systems seems to work fine, but the touchpad is slow and extremely buggy.

Here is an excerpt from my xorg.conf file:

```
Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto"
        Option "MinSpeed" "0.45"
        Option "MaxSpeed" "0.90"
        Option "AccelFactor" "0.5"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "SHMConfig" "true"
EndSection
```

I put that section in my xorg.conf and it still did not work. I then added i8042.nomux=1 to my menu.lst for grub, and that only made things worse. After doing an update-grub and rebooting, touchpad did not work at all, and keyboard was intermittent, often typing in random junk. I had BIOS revision A09 and downgraded to A08 to see if that would help, but still the same thing. Taking out the i8042.nomux line did not help, so I set i8042.nomux=0 and that puts me back at square one: a working touchpad that is extremely slow. Just trying to see if anyone else has any ideas on how to fix this.

---

