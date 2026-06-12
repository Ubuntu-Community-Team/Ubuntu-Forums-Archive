---
title: "Touchpad &quot;Disable while typing&quot; doesn't work"
date: 2015-04-03
forum: Hardware
---

### Post by jgradyc on 2015-04-03
I'm running Crouton with Ubuntu 14.04 (trusty and unity) on a Chromebook ASUS C300M.  I have the "Disable while typing" box checked on the settings for touchpad, but when the palms of my hands touch the touchpad, the cursor moves and often starts one of the applications from the launcher on the left side of the screen. On other occasions, it will move the cursor somewhere else in the text and continue typing from there, so I have to go back and edit those mistakes.

How can I get the "Disable" to work? Or, how can I extend the time it is disabled after a keystroke? If it is disabled, it's only for a fraction of a second. As a last resort, I've disabled the entire touchpad and I am using a mouse, but I'd prefer not to have to do that. 

By the way, the exact same problem exists running Crouton with Ubuntu, KDE, XFCE, and mint on the Acer C710.

---

### Post by Keith_Helms on 2015-04-03
One thing to try is a startup script to configure the touchpad.   I had a  similar problem to you and set up a script with the following commands  in it.

```
#/bin/bash

/usr/bin/synclient PalmDetect=1
/usr/bin/synclient PalmMinWidth=5
/usr/bin/synclient RTCornerButton=0
/usr/bin/synclient RBCornerButton=0
/usr/bin/synclient ClickFinger1=0
/usr/bin/synclient ClickFinger2=0
/usr/bin/synclient VertEdgeScroll=0
/usr/bin/synclient HorizEdgeScroll=0
```

---

