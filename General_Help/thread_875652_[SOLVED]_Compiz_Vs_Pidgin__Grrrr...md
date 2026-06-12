---
title: "[SOLVED] Compiz Vs Pidgin :: Grrrr.."
date: 2008-07-31
forum: General Help
---

### Post by Syndacate on 2008-07-31
Hey,

I use compiz's "placement" function - I like all my windows to drop in the center of the screen (I'm a bit OCD like that).

Though when I close pidgin to the system tray - then open it back up, it drops it in the center of the screen!

There any way I can either:
A)  Create an exception for certain windows in compiz (I checked the settings for the "put" option, but none that I could tell to that effect.
B)  Make pidgin dock so it'll always snap to that side of the screen?

Hehe.

I like my pidgin window docked on the right side of my screen, but I like all my windows that pop-up to pop-up in the center.  Ahh, there has to be some way I can create an exception in compiz.

Anybody?

---

### Post by overdrank on 2008-07-31
moved to  Desktop Effects & Customization  
:)

---

### Post by Syndacate on 2008-07-31
*Bump.

How am I the only one with this problem?

---

### Post by DaymItzJack on 2008-07-31
How did you manage to get them to all go in the middle?

Depending on how you did that, you could try to:

Open "Place" plugin for compiz, go to the "Fixed Window Placement" tab and put:

title=Buddy List
x = 2
y = 24 (or whatever..)

for the left side of the screen.

---

### Post by Syndacate on 2008-07-31
> **DaymItzJack said:**
> How did you manage to get them to all go in the middle?

Depending on how you did that, you could try to:

Open "Place" plugin for compiz, go to the "Fixed Window Placement" tab and put:

title=Buddy List
x = 2
y = 24 (or whatever..)

for the left side of the screen.

I got them all did that by using the placement option to drop all windows in the center.

I set it fixed, title=Buddy List with X at max (slider all the way to the right) and Y at min (slider all the way to the left) and it worked 100%.

Thank you very much!

EDIT:
For other people looking at this:
Once you select the "*Fixed Window Placement*" tab in the "*Place Windows*" feature of compiz, select "*New*" under "*Windows with fixed positions*," a dialog will pop up.  In the dialog, click the *plus* sign to add a new feature, for *Type*, select "*Window Title*," and for value, type in "Buddy List" (no quotes), leave the other default values and hit "*Add*."  Then the two sliders are for X and Y coordinates, for all the way on the left side, slide the *X* slider all the way to the left, and opposite for the right side.  Remember, if you want it justified to the top, make sure the *Y* slider is at the minimum.

---

