---
title: "Keyboard Media Controls"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by gerowen on 2006-11-03
As some of you may or may not know from a couple of my other posts, I use a keyboard with lots and lots of shortcut keys and media controls on it.  The shortcut keys work and the volume control keys work, but some of the keys do not work, and I do not quite know how to bind them to specific actions.  Is there an easy way to do this in Gnome?  In specific the keys that do not work are the play/pause, stop, skip forward and skip back, and the media player launching button.  Now I'm new-ish to Gnome, but I find that it runs smoother and I just like its feel better, but in KDE I could just go to Keyboard shortcuts in the Control Center and bind the one to launch the media player as an application shortcut, but I'm not sure how to do that in Gnome, let alone the other ones I mentioned.

---

### Post by chriscando on 2006-11-03
I was able to do it on my Dell XPS m1210 using xev and xmodmap. I used xev to find the keycodes and then mapped them to keys like F18, F19, etc.
Here is my config file for xmodmap called remapkeys
then just run xmodmap to instantly change the keys, xmodmap remapkeys

```
keycode 160 = F14
keycode 174 = F15
keycode 176 = F16
keycode 162 = F17
keycode 144 = F18
keycode 153 = F19
keycode 164 = F20

```

---

### Post by Cuppa-Chino on 2006-11-13
tried running xev but this is what happens (does not make me any cleverer)

**Multimedia key Next Track**
output seems to make sense to me
```
KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x136, subw 0x0, time 3765506749, (1294,435), root:(1306,530),
    state 0x10, keycode 144 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x136, subw 0x0, time 3765506925, (1294,435), root:(1306,530),
    state 0x10, keycode 144 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

**Multimedia key Volume UP and then Volume DOWN**
there is no keycode no nothing therefore I am not clear on how to change this...

```
FocusOut event, serial 29, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 29, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 29, synthetic NO, window 0x3200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 29, synthetic NO, window 0x3200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```


Any help is appreciated

---

