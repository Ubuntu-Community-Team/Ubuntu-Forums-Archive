---
title: "limit/reduce laptop screen (partly broken)"
date: 2012-01-02
forum: Hardware
---

### Post by Pifilatakanemu on 2012-01-02
Hi,

I have a laptop with a partly broken screen. about 20% on the right and at the top are not working anymore.

I suppose I can limit the screen to the intact part with xrandr.

I tried the following command:

> ulrike@ulrikes:~$ xrandr --output LVDS1 --fb 900x700+0+0

The size of the screen is reduced although I get an error message

> xrandr: specified screen 900x700 not large enough for output LVDS1 (1280x800+0+0)
The problem is, that the "virtual screen" extends further. The unity bar for example extends until the right edge, so I can't properly access the buttons there as I don't see them.

Is there any other solution or additional commands to reduce the size of the screen "on all levels"?

In addition, I can't define the distance from the top which is necessary as the first 20 pixels at the top are broken, too.

I want Ubuntu to only use the defined area.


Thanks!

---

### Post by jerrrys on 2012-01-03
Try **Ctrl Alt -**  or  [B]Ctrl Alt +


[/B]

---

### Post by Pifilatakanemu on 2012-01-03
Thanks for the hint, but what are these combinations about?

---

### Post by jerrrys on 2012-01-03
This will reduce or enlarge screen size and just may give you something useful.

---

### Post by N00b-un-2 on 2012-01-03
you may want to try scaling

---

### Post by Pifilatakanemu on 2012-01-03
Thanks for the hintes.

CTRL+Alt+"+" and +"-" didn't do anything. 

And I couldn't think of using scaling in order to solve my problem.

I can't even add an additional panel at the right side under 11.10...


Edit:

I installed Gnome and now I arranged to add a panel to the right site.

---

### Post by jerrrys on 2012-01-03
I have used that shortcut in the past and didn't try it; your right it no longer works.  My apologizes, but glad you found something that works.

---

