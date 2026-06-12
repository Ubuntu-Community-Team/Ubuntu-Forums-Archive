---
title: "How to make the wacom buttons hold instead of click"
date: 2011-11-29
forum: Hardware
---

### Post by lionbeast on 2011-11-29
Hi, i have a cintiq, and most application like gimp, mypaint etc use the space bar to navigate in the canvas. so i set one of the cintiq buttons to be space. but the problem is that when i clic the button, instead of holding space, it presses space and then lets go immediatly, like a click. Is there a possiblity to change that?

---

### Post by Favux on 2011-11-29
Hi lionbeast,

Are you using a xsetwacom command?  What does it look like?

What release of Ubuntu are you using?  What's the xf86-input-wacom version?
```
xsetwacom -V
```

---

### Post by lionbeast on 2011-11-29
Hi thanks for the quick reply.

I'm on the latest ubuntu, oneiric ocelot

here is what xsetwacom -V returns:
0.11.0

my script:

```
xsetwacom set "Wacom Cintiq 12WX stylus" Button 3 "key e"
xsetwacom set "Wacom Cintiq 12WX stylus" Button 2 "key e"

xsetwacom set "Wacom Cintiq 12WX stylus" TabletPCButton "off"
xsetwacom set "Wacom Cintiq 12WX stylus" PressureCurve "0 5 60 100"

xsetwacom set "Wacom Cintiq 12WX pad" StripLeftUp "key d"
xsetwacom set "Wacom Cintiq 12WX pad" StripLeftDown "key f"
xsetwacom set "Wacom Cintiq 12WX pad" StripRightUp "key ."
xsetwacom set "Wacom Cintiq 12WX pad" StripRightDown "key ,"


xsetwacom set "Wacom Cintiq 12WX pad" Button 13 "key r"
xsetwacom set "Wacom Cintiq 12WX pad" Button 3 "key z"
xsetwacom set "Wacom Cintiq 12WX pad" Button 1 "key ctrl left"
xsetwacom set "Wacom Cintiq 12WX pad" Button 2 "key ctrl right"
xsetwacom set "Wacom Cintiq 12WX pad" Button 8 "key space"


xsetwacom set "Wacom Cintiq 12WX pad" Button 14 "key f"
xsetwacom set "Wacom Cintiq 12WX pad" Button 11 "key shift ctrl o"
xsetwacom set "Wacom Cintiq 12WX pad" Button 9 "key ctrl d"
xsetwacom set "Wacom Cintiq 12WX pad" Button 10 "key ctrl t"
xsetwacom set "Wacom Cintiq 12WX pad" Button 12 "key ctrl s"



xsetwacom set "Wacom Cintiq 12WX eraser" Button 1 "key i"

```

as you can see in my script button 8 is set to space. and if i try it in an editor. it will make a space. so the command works. but if i hold the button 8 pressed, it won't hold space pressed.

---

### Post by Favux on 2011-11-29
Thanks for the script.

If either Button 2 or Button 3 on the stylus is set to a middle click i.e. 2 that is grab in Gimp.  I find that easier than using a tablet button.
```
xsetwacom set "Wacom Cintiq 12WX stylus" Button 3 2
```
instead of "key e".

While it might be theoretically possible to do it through the buttons, doesn't seem like a good idea.  Xsetwacom is designed to force a button release at the end of a command.  So you'd have to probably take two buttons, one as space down and the other as space up and pass that directly into the driver.  Definitely a I don't want to go there sort of thing.

---

### Post by lionbeast on 2011-11-30
Oh thanks, i didn't know that. Ok that also works in mypaint, so i'm all set to paint haha. Thank you very much.

---

