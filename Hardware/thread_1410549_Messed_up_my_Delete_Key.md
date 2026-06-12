---
title: "Messed up my Delete Key"
date: 2010-02-18
forum: Hardware
---

### Post by SoundGuy.Jon on 2010-02-18
I was messing around with keyboard shortcuts, and accidentally assigned the delete key to something other than delete. I went back into keyboard shortcuts and unassigned it from that, but now it does absolutely nothing.
I'm on a Compaq Presario C500 laptop, running Ubuntu 9.10 Karmic Koala. Everything is up to date.
I tried using xev to get the output of the delete key, and this is what it gave me
```
FocusOut event, serial 36, synthetic NO, window 0x7c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x7c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ClientMessage event, serial 36, synthetic YES, window 0x7c00001,
    message_type 0x131 (WM_PROTOCOLS), format 32, message 0x12f (WM_DELETE_WINDOW)

```I've also gone into Preferences > Keyboard and changed the keyboard and layout, then reset to default, but still nothing. Any suggestions? Or am I forever screwed?

---

### Post by lidex on 2010-02-19
Did you assign it as a custom shortcut (in keyboard shortcuts)? If so try removing it and rebooting.

---

### Post by falconindy on 2010-02-19
What's the output of 'xmodmap -pk'?

---

### Post by SoundGuy.Jon on 2010-02-19
> **lidex said:**
> Did you assign it as a custom shortcut (in keyboard shortcuts)? If so try removing it and rebooting.
In fact I did. At first I didn't think that it worked, even after rebooting. But after double checking it turns out I didn't delete the custom shortcut assignment in keyboard shortcuts. So removing it from there and rebooting did the trick afterall. I have my Delete key back!

---

