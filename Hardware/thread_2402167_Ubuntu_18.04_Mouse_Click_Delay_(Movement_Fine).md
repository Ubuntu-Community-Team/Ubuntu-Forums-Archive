---
title: "Ubuntu 18.04 Mouse Click Delay (Movement Fine)"
date: 2018-09-26
forum: Hardware
---

### Post by courtalj on 2018-09-26
Hello,

There is a noticeable delay after a mouse click to when the click takes effect. It makes highlighting code very tedious sometimes. It seems to be on the order of ~100ms, though I have no way to measure. Mouse movement is perfectly responsive, and there are no keyboard issues.

I am running a fully up-to-date Ubuntu Mate 18.04 environment on a Huawei Matebook X Pro laptop. It is docked to a CalDigit Thunderbolt 3 Dock, mouse and keyboard and monitor plugged into that. To reiterate: the keyboard has no delay whatsoever, nor does mouse movement (I am extremely sensitive to mouse movement lag). The issue only affects clicking.

Things I have already ruled out: disabling the touchpad completely, disabling middle-click emulation using gnome-tweaks, "apt install xserver-xorg-input-synaptics" & reboot, and changing all the "Mouse Preferences".

Here is the output of "xinput list":

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYNA2393:00 06CB:19AC                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SYNA1D31:00 06CB:CD48 Touchpad              id=12    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=14    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Ornata Chroma                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Ornata Chroma                   id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HD Camera: HD Camera                        id=10    [slave  keyboard (3)]
    &#8627; CalDigit, Inc. CalDigit Thunderbolt 3 Audio    id=13    [slave  keyboard (3)]
    &#8627; Razer Razer Ornata Chroma                   id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=18    [slave  keyboard (3)]
    &#8627; Razer Razer Ornata Chroma                   id=19    [slave  keyboard (3)]
```

---

