---
title: "Multimedia key help (Gateway MA7 laptop)"
date: 2008-06-21
forum: Hardware
---

### Post by jokermatt999 on 2008-06-21
I've been having trouble with my multimedia keys on my laptop. Strangely enough, the keys for brightness, volume up, volume down, and mute already work. I just can't get the play/pause, stop, next, and previous keys to work. I can set them to shortcuts through the Keyboard Shortcuts dialogue, but they aren't recognized by anything else. xev outputs:

> FocusOut event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

when I press any of the media keys. I tried KeyTouch, but I couldn't find the right keyboard. So I tried KeyTouch Editor, but I couldn't seem to get it to react to my multimedia keys whatsoever.

Please help! :(

PS: This is mostly in gnome, but I can't seem to get them to work when I switch to fluxbox either. I'd actually prefer help on fluxbox, but I really just want these things to work!

---

