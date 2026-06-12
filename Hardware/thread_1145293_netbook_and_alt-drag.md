---
title: "netbook and alt-drag"
date: 2009-05-01
forum: Hardware
---

### Post by gregstyles on 2009-05-01
computer = Asus eee pc 701 4g

I installed Ubuntu 9.04 and it works great. except....

problem:  With the netbook's 800x468 screen, I need to alt-drag windows up to get to the OK/NEXT button at the bottom of the window.  Ubuntu won't let me drag it above the top of the screen so I can't get to the buttons at the bottom.

any suggestions

---

### Post by FlyingBuzz on 2009-05-01
I've discovered that if you turn off advanced desktop effects (compiz) you can easily drag the window up as far as you want.
When compiz's enabled I can't move any window through the top of the screen.
I'm using Asus Eee PC 901 20 Gb

---

### Post by gregstyles on 2009-05-01
That worked - Thanks.

System - pref. - appearance - visual effects - none

---

### Post by practic on 2009-05-02
There's at least one other way that doesn't require turning off desktop effects:

1. Go to Compiz Config Settings Manager (you'll need to install it if it doesn't show up under Preferences), then choose General Options.  

2. Click on Desktop Size and set Vertical Virtual Size to at least 2.

Now when a dialog stretches below the screen you can switch to the lower vertical virtual desktop area to access the buttons.  If you have Expo enabled in Compiz Config Settings Manager, this is quite easy.  Press <Super> (windows key) and E to display the desktops, then use either the arrow keys or the mouse to select the active one...or make one of the screen corners activate Expo (you can do that in the Expo module).

---

### Post by dnairb on 2009-05-03
I don't know if this works on the UNR, (it works on a straight Ubuntu install on my 701) but you could try the following in terminal (so you can still have desktop effects enabled):

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

---

### Post by practic on 2009-05-03
Ah, I knew it would be hidden away somewhere in Compiz! 

For those who want to go through Compiz Config Settings Manager, it is under the "Move Windows" module, and uncheck the option called "Constrain Y".

Then windows can be moved either by Alt and Left Mouse button, or by Alt and F7, then use the arrow keys to move the window (handy if you want to keep your hands on the keyboard)...that is, assuming your shortcuts are set to default...check them while you are in the Move Windows dialog.

---

### Post by VictorR on 2009-05-03
On Asus EEE PC 701 I just changed Alt+F7 (Move window shortcut) to Alt+Super L (Home button between Fn and Alt).

---

