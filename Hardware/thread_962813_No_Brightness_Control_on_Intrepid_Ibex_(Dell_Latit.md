---
title: "No Brightness Control on Intrepid Ibex (Dell Latitude C610)"
date: 2008-10-29
forum: Hardware
---

### Post by Ric_NYC on 2008-10-29
I've tried everything (EnvyNG, editing Xorg)... Intrepid Ibex doesn't recognize the video card!

It works when I use Hardy Heron.


Any help is appreciated.

Thanks!

---

### Post by anamorgan on 2008-10-29
Look up for the Fn button in blue or red, depends on yuor model. Use that with the any light sign in function or arrow keys of the keyboard. It might not be teh case of vedio card, i guess so, beacuse any problems in the vedio card wouldnt give you teh display in teh first place.

---

### Post by Ric_NYC on 2008-10-29
> **anamorgan said:**
> Look up for the Fn button in blue or red, depends on yuor model. Use that with the any light sign in function or arrow keys of the keyboard. It might not be teh case of vedio card, i guess so, beacuse any problems in the vedio card wouldnt give you teh display in teh first place.


The "function key" (fn) doesn't work.
:(

---

### Post by LucasHenderson on 2008-11-03
I think this may be a problem with Xorg, though i can't be sure. I have a c610 as well, and I cannot use the the function keys to control brightness either, when running everything regularly, however, I have found that they do work when you switch to a console (Ctrl+Alt+F1). They also work while booting, up until the point where the GUI is loaded.
I haven't done enough searching, but if it hasn't already been posted, I plan to submit this as a bug.

---

### Post by Ric_NYC on 2008-11-05
> **LucasHenderson said:**
> I think this may be a problem with Xorg, though i can't be sure. I have a c610 as well, and I cannot use the the function keys to control brightness either, when running everything regularly, however, I have found that they do work when you switch to a console (Ctrl+Alt+F1). **They also work while booting, up until the point where the GUI is loaded**.
I haven't done enough searching, but if it hasn't already been posted, I plan to submit this as a bug.


I noticed that too.

Something was done right on Hardy Heron... Now it is broken!

Thanks for replying.
If someone finds a way to fix it, please let's know!

---

### Post by LucasHenderson on 2008-11-07
Something new I discovered today: When in Low Graphics Mode(a result of me making a typo in xorg.conf), the function keys work. I'm certainly no expert, but perhaps this means there is something wrong with the ati/radeon driver?

---

### Post by hac13 on 2008-11-12
I have the same model and now the exact same bug. Have you had any luck yet? It's not a huge inconvenience to switch to a console and back for now, but I hope I can find a way to fix it soon.

---

### Post by binbash on 2008-11-12
Did you try this ? : 

[http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora](http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora)

---

### Post by Ric_NYC on 2008-11-12
> **hac13 said:**
> I have the same model and now the exact same bug. **Have you had any luck yet?** It's not a huge inconvenience to switch to a console and back for now, but I hope I can find a way to fix it soon.

No solution yet.

Should we go back to Hardy Heron? :confused:

---

### Post by hac13 on 2008-11-12
> **binbash said:**
> Did you try this ? : 

[http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora](http://www.howtoforge.com/manage-your-laptop-hotkeys-on-fedora)

Thanks for the instructions, but for some reason I can't even my brightness keys to generate an event. (ACPI or a keycode) :confused:

> **Ric_NYC said:**
> No solution yet.

Should we go back to Hardy Heron? :confused:

There's no going back for me (no time to downgrade) but maybe it's the only solution for now.

---

