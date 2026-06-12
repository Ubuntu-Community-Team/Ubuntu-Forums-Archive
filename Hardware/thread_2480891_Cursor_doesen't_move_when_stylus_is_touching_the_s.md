---
title: "Cursor doesen't move when stylus is touching the screen"
date: 2022-11-13
forum: Hardware
---

### Post by chr-s on 2022-11-13
I'm using a convertible one mix 4 laptop.
There is a bug in how stylus events are handled. 
I can move the cursor by dragging the stylus above the screen but the moment I touch the stylus to the screen (i.e. it would normally generate a pendown event) the cursor stops moving till I lift the stylus.
However, the stylus works as expected if I hold either of the physical buttons down.

The problem persists with different styluses, from different manufacturers, and for both xorg and wayland, and for KDE and gnome.

It works as expected when booting to windows.

xinput ouput:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYNA3602:00 0911:5288 Mouse                 id=10    [slave  pointer  (2)]
&#9116;   &#8627; SYNA3602:00 0911:5288 Touchpad              id=11    [slave  pointer  (2)]
&#9116;   &#8627; GXTP7386:00 27C6:011A                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; GXTP7386:00 27C6:011A Stylus Pen (0)        id=16    [slave  pointer  (2)]
&#9116;   &#8627; GXTP7386:00 27C6:011A Stylus Eraser (0)     id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; GXTP7386:00 27C6:011A Stylus                id=13    [slave  keyboard (3)]
    &#8627; GXTP7386:00 27C6:011A Keyboard              id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]

---

