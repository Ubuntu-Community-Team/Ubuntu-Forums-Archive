---
title: "Ubuntu 15.10 Synaptics Touchpad stops working moments after login appears"
date: 2016-04-05
forum: Hardware
---

### Post by wolfcoder2 on 2016-04-05
Using Ubuntu 15.10 with MATE

This is an issue unique to Ubuntu.
The touchpad works fine in Debian MATE or Linux Mint MATE, but I don't want to use those distros.

One day, the touchpad started to have jerky behaviour and then suddenly quick working. Now, ever since rebooting, the touchpad will work for moments when the login screen appears, but then will stop working. This occurs after a full boot (logging in and out won't make the touchpad work for a brief moment again).

*I don't actually log in, it works during the login prompt for a moment and just stops without me doing anything else other than moving the pointer around*. This is not the touchpad stopping after logging in.

Uninstalling xserver-xorg-input-synaptics does disable the touchpad. Reinstalling xserver-xorg-input-synaptics does not fix the issue.

I've tried the modprobe proto thing which does nothing, I've tried the dconf and settings thing where you do touchpad enabled. It was already enabled everywhere it was mentioned and this does nothing.
The synclient thing doesn't work either and the touchpad is already not disabled.

I've spent hours Googling through fixes from this community, other similar distros, etc. and I see fixes that work for many people, but not me.

The xinput list is:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                            id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M325                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; DLL07BD:00 06CB:75BF UNKNOWN                id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]

```

This occurs even when booting without my USB mouse plugged in.

This is a DELL Inspiron 17 5000-series laptop. It does NOT have any of those function keys you would use to turn the touchpad on and off. I tried holding FN and pressing the function keys anyways, none of them turn the touchpad on or off.

Any help with this would be greatly appreciated.

---

### Post by wolfcoder2 on 2016-04-06
An update to Ubuntu (just now) arrived. After installing it, the touchpad is behaving again.

---

