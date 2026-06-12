---
title: "Problem with compiz rotate cube and draw fire"
date: 2008-08-21
forum: General Help
---

### Post by rzax2 on 2008-08-21
Hi all

First off, I just want to say I am new to Ubuntu and Linux (have been using is for 3 weeks now) and I love it.

The problem I am having is in order to use rotate cube and draw fire, i MUST be on top of a window from an app in order for it to work.  When i use the key command to rotate the cube on top of a window (say, firefox for example) it works fine.  On the other hand, when i go to use the command, or just roll the mouse wheel while my mouse is hovering over the desktop, it wont work.  If i use the ctrl-alt-mouse1 command, it just begins to draw a box like the ctrl-alt wasnt even being pressed.  This also applies for drawing fire.  All other effects work correctly

Interesting enough, this problem didnt occur with my original setup, but as soon as I added a third display.  Originally I had 2 lcd monitors running on a geforce pcie-16x 8800gt running with full settings and I was able to use both effects mentioned before as they were intended..  I now have added a geforce fx 5200 pci which is running to my samsung hdtv.  The 5200 has no effects running on it, and all other effects work fine on the 8800gt, just in order to get the fire/cube rotate to work, the mouse has to hover about a window prior to entering the hotkeys.

I am also running this script on load in order to eliminate menu lag caused by running compiz on dual monitors:

```
#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.0 emerald --replace &
sleep 10 &
DISPLAY=:0.1 emerald --replace &
```

If you need me to post any more information, please let me know.  Any help on this would be greatly appreciated!

---

