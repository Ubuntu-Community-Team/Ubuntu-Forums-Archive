---
title: "multi button mouse with HAL"
date: 2009-11-18
forum: Hardware
---

### Post by Felson on 2009-11-18
Not sure if this is just kbuntu, but I just upgraded to Karmic and I cent get my side buttons to work on my mouse.
I have a Logitech MX500 mouse. Before the upgrade I had fixed the xorg.conf file, and was using xbindkeys to make the buttons do "alt-left" and "alt-right"
After the upgrade, it comments out the stuff for the mouse. I un-commented the lines, and still no good. When checking my mouse with xev, the 2 side buttons are detected as clicked, but return no "button #" to identify them with. Is there something I need to do with HAL to fix it? or is there a way to make HAL not deal with the mouse, and give it back to xorg?

Here is the output from xev:
Forward button
```

EnterNotify event, serial 28, synthetic NO, window 0x4400001,
    root 0x13c, subw 0x0, time 39868843, (151,160), root:(1435,185),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,      
    focus YES, state 16                                             

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  60  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Back Button
```

EnterNotify event, serial 28, synthetic NO, window 0x4400001,
    root 0x13c, subw 0x0, time 39870745, (150,160), root:(1434,185),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,      
    focus YES, state 16                                             

KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  60  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

---

### Post by diesch on 2009-11-18
See [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) for how to configure your mouse using HAL.

---

### Post by mshelton on 2009-11-20
> **diesch said:**
> See [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) for how to configure your mouse using HAL.


After x amount of years with xorg and now hal, why hasn't someone written a gui for this?

---

### Post by diesch on 2009-11-20
Configure X.org input devices using HAL isn't around for that long and it's not a task most people do often.

But I included it in my list of "things I'll do if I have time" :-) Do you have an idea how a GUI should look like?

---

### Post by Felson on 2009-11-25
ok... Now I don't think it is a HAL problem. at least not in a ".fdi" file anyway.
If I play with xev, all my buttons have "Button #" when they are clicked except my side buttons. according to "xinput query-state" while holding them down, they should be buttons 8 and 9. If I use "xinput set-button-map" to change there button numbers (1 2 3 4 5 6 7 15 16 10 11 12 13 14 8 9) they show up as Buttons on xev. It looks like something is blocking buttons 8 and 9. Now I "could" set up a map like the above to fix it, and just call them 15 and 16 but I would rather find why I can't use buttons 8 and 9 in the first place.

---

### Post by Felson on 2009-11-25
OMG!!! I found my problem... Turns out that the problem was me... before the upgrade I was running xbindkeys to bind button 8 and 9. This was fine, except that they moved "xvkbd" from "/usr/X11R6/bin/" to "/usr/bin/xvkbd".
So really, just a noobtastic error on my part. Thanks for the input from those that tried to help me. The up side, is that I understand the HAl config files now :)

---

