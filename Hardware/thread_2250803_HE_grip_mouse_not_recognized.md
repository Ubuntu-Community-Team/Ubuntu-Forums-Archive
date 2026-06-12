---
title: "HE grip mouse not recognized"
date: 2014-10-31
forum: Hardware
---

### Post by squiq2 on 2014-10-31
Im trying to use my R-go tools HE grip mouse in ubuntu, which works fine in windows.
I tried modprobe psmouse and xinput list, but the mouse won't show up..

(It seems to me that is could be the PS/2 Generic Mouse but if I unplug the mouse, is stays on the list so its not that one? If I unplug my logitech mouse it dissapears from the list. )

&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech Illuminated Keyboard     id=11   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                   id=14   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                         id=16   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad

It seems that ubuntu is not recognizing the mouse at all?

anyone an idea what to do?

thanks in advance!

---

### Post by squiq2 on 2014-10-31
Solved!

It suddenly worked. Maybe a faulty connection?

---

