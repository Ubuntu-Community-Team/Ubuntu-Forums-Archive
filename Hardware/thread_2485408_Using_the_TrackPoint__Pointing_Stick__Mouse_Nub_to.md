---
title: "Using the TrackPoint / Pointing Stick / Mouse Nub to scroll only"
date: 2023-03-28
forum: Hardware
---

### Post by wiel0033 on 2023-03-28
Hello - 

I installed Ubuntu 22.04 on a zbook and am trying to get the mouse / pointer setup.  Does anyone know if it's possible to separate the trackpoint from the touchpad?  The idea would be for the touchpad to function as it normally would, but for the trackpoint to just be for scrolling.  From what I can tell they are one and the same from a system perspective - both map to #7 in xinput.

Thanks!

xinput list
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:16                         id=6    [slave  pointer  (2)]
**&#9116;   &#8627; xwayland-relative-pointer:16                id=7    [slave  pointer  (2)]**
&#9116;   &#8627; xwayland-pointer-gestures:16                id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:16                        id=9    [slave  keyboard (3)]

---

