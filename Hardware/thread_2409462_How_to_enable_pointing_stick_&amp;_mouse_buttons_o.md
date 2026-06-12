---
title: "How to enable pointing stick &amp; mouse buttons on toshiba laptop?"
date: 2019-01-02
forum: Hardware
---

### Post by doug21 on 2019-01-02
I have a new install of Ubuntu 18.04.1 on a new Toshiba Tecra X40 laptop. The point stick, and the two mouse buttons seemingly associated with it, don't do anything.

The touchpad works fine at controlling the mouse pointer and left click, but there is no right click function anywhere.

Can I enable the two currently redundant mouse buttons? They have a better feel than the click on the touchpad. Is there a right click to be enabled on the touch pad?

My xinput list looks like this, and I tried the instructions [here]("https://superuser.com/questions/109504/how-do-i-enable-a-stick-pointing-device-in-ubuntu") to enable the Virtual core XTEST pointer device without success.

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Melfas LGDisplay Incell Touch               id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD: TOSHIB             id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=13    [slave  keyboard (3)]

Thanks for any help!

---

### Post by doug21 on 2019-01-03
I've used Gnome Tweaks to get a right click function on the touchpad, and discovered that the menu key functions a bit like a right click.

Further searching suggests [same problem]("https://bugzilla.redhat.com/show_bug.cgi?id=1572625") with pointing stick and buttons with at least one other toshiba model, and no solution created.

---

