---
title: "Yet another Synaptics touchpad problem"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by pilleboksen on 2007-11-01
After upgrading to Xubuntu 7.10 my Synaptics touchpad has started to behave strangely.
In order to make the cursor move at all I have to start the movement at either the left or  right edge of the touchpad.
If I start by placing my finger in the middle of the touchpad, the cursor doesn't move at all.
Even xev reports nothing when i do this. 
Please help or let me know if more information is needed.

from xorg.conf:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"     "on"
EndSection

```

from dmesg:
```

Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
*couple of lines cut*
input: SynPS/2 Synaptics TouchPad as /class/input/input4

```

---

### Post by pilleboksen on 2007-11-09
Nobody able to point me in the right direction?
Just for the record, I have searched these forums and I have asked Google.
But so far I've been unable to find this problem anywhere else. Could this be as
simple as a configuration problem?

---

### Post by fragos on 2007-11-10
> **pilleboksen said:**
> Nobody able to point me in the right direction?
Just for the record, I have searched these forums and I have asked Google.
But so far I've been unable to find this problem anywhere else. Could this be as
simple as a configuration problem?

I have USB connected touch pad that worked well after being added to my 7.04 xorg.conf.  I did a clean install of 7.10 and that touchpad works without adding anything to xorg.

---

### Post by pilleboksen on 2007-11-11
I forgot to mention that the machine in question is a laptop (Asus V6J)

---

### Post by fragos on 2007-11-11
I just purchased a Dell 1420n with Ubuntu 7.04 and the touch pat functions well but I found the on pad tapping to be difficult for me to master the feel of.  Cursor movement functions perfectly, even when gently rolling my finger.  I installed gsynaptics to disable the the taps.  I'm waiting for Dell to release the 7.10 update before upgrading

---

