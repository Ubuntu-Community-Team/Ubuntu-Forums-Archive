---
title: "Flipped my screen by accident"
date: 2008-08-02
forum: General Help
---

### Post by Thirtysixway on 2008-08-02
Alright I installed ubuntu but the resolution was wrong so I went to Screen Resolution in the menu to change it.  I couldn't see the whole window so I just tab > enter'd until it changed.

Well it ended up flipping the screen 90 degrees counter-clockwise.  I can't get to the menus or anything (I'm pretty sure they're offscreen).

What file can I edit to flip this back?  I'm kind of stuck here because the default resolution is too messed up to read a text editor.
:popcorn:

---

### Post by rEbyTer on 2008-08-02
First of all flip your screen so you could see what is happening on the screen.

Type this in a terminal:
```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

Go to screen resolution again and with **ALT+click** move your windows to see the options.

---

### Post by Thirtysixway on 2008-08-02
Didn't work :\
All well.  It was a wubi install anway.  The Wubi uninstaller doesn't want to run but I'll figure this out. Thanks

---

### Post by rEbyTer on 2008-08-02
What didn't work ? Can you please explain me more advanced ? and give me some screenshots ? thanks

---

### Post by Thirtysixway on 2008-08-02
I can't really give screenshots because it's on the same computer.

When I boot up ubuntu, the resolution is too small so when I logged in I changed it, but also flipped the screen.  When I login now, it flips 90 degrees counter-clockwise and the rest of the desktop doesn't load (wallpaper, menus, etc).

I found a login option that would load up console, and I typed in the command above.  Then I restarted X but it didn't seem to do anything.

---

### Post by rEbyTer on 2008-08-03
With that command you are able to move windows on top of screen like this

---

