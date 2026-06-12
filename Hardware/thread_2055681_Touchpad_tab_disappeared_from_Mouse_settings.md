---
title: "Touchpad tab disappeared from Mouse settings"
date: 2012-09-09
forum: Hardware
---

### Post by wc2351 on 2012-09-09
Hi all,

I recently installed Ubuntu 12.04 LTS (64 bit) on my Samsung Series 9 NP900X3B (dual boot with Windows). After the install the touchpad was working out of the box but the right click didn't seem to work after some time, so I found this command on a different thread and ran it: 

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe


After this the right click worked okay, but the two-finger scroll was disabled and I found out that the entire Touchpad tab from Mouse and Touchpad Settings was missing.  Here's what I get from xinput list:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Webcam SC-13HDL11624N                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

My touchpad is working fine other than the two-finger scroll thing, and it seems like it is now being detected as a mouse. Could someone help me solve this problem?

---

### Post by joncar94 on 2012-09-30
:lolflag: ¡Yes I have the same problem! I'm crazy to get a solution for it, but I had not recognized anything on my computer! ¡Please! ¡Help me! ):P

---

### Post by dhruvwali on 2013-01-04
> **wc2351 said:**
> Hi all,

I recently installed Ubuntu 12.04 LTS (64 bit) on my Samsung Series 9 NP900X3B (dual boot with Windows). After the install the touchpad was working out of the box but the right click didn't seem to work after some time, so I found this command on a different thread and ran it: 

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe


After this the right click worked okay, but the two-finger scroll was disabled and I found out that the entire Touchpad tab from Mouse and Touchpad Settings was missing.  Here's what I get from xinput list:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Webcam SC-13HDL11624N                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

My touchpad is working fine other than the two-finger scroll thing, and it seems like it is now being detected as a mouse. Could someone help me solve this problem?

Any update?

---

