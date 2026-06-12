---
title: "Please Help with maping Slate Pc external buttons"
date: 2012-07-26
forum: Hardware
---

### Post by pixelatedragon on 2012-07-26
Being that this is my first thread I would like to say thank you to every one on this forum.  I have used Ubuntu forums to solve almost every problem I have had with Ubuntu and I have been using Ubuntu for what seems like forever.  Now on to the issue at hand.  

I recently bought a ASUS Eee Slate B121 and promptly installed Ubuntu 12.04.  Almost everything worked out of the box except the button to activate the onscreen keyboard and the window switcher button.  For the last few days I have been trying to get them to work but I have run in to an issue that I can't seem to get around.  I googled how to map laptop keys and came up with a solution using xev and xmodmap this seemed to work for the first but when i tried the second... Problem

Using showkey the two buttons show the exact same output:

0x00 0x81 0xf0 0x80 0x81 0xf0 
0x00 0x81 0xf0 0x80 0x81 0xf0

Using xev the output seems to be identical as well:

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  56  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967286 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x4c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

I should mention that the xev output looked different before I  used xmodmap to map one of the buttons to F13 with:
xmodmap -e "keycode 246 = F13"

If any one could help I would be very thankful and once again thank you everyone on Ubuntu Forums.

---

