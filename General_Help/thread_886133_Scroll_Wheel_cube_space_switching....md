---
title: "Scroll Wheel cube space switching..."
date: 2008-08-10
forum: General Help
---

### Post by ems5311 on 2008-08-10
Just installed Hardy yesterday on my macbook Santa Rosa (was up until 4 am with it, actually), and I love it.  One small problem I've just run into though.

I noticed that when I scroll my scroll wheel down (with a usb mouse hooked up, of course) while the cursor is on the desktop, my cube flips to the right one.  I've got compiz and all the functions set up to work fine, but I can't find where my mouse scroll wheel got bound to "flip cube right".  If I scroll up the cube does _not_ flip left.  If I click the scroll wheel, rotate cube is initiated (which I am fine with).

Anyone know how to disable this scroll wheel cube flipping?

Here is a picture of my rotate cube settings (as you can see, nothing has to do with the scroll wheel).  Everything is disabled in the other two menus.

Thanks in advance.

---

### Post by issih on 2008-08-10
Yup, I found this one...I think the settings are in the viewportswitcher plugin. Something lke switch to viewport left and right set up as button 4 and 5 - i.e. scroll wheel.

Either disable the whole plugin or just change those specific actions and it all goes away.

Hope that helps.

---

### Post by ems5311 on 2008-08-10
> **issih said:**
> Yup, I found this one...I think the settings are in the viewportswitcher plugin. Something lke switch to viewport left and right set up as button 4 and 5 - i.e. scroll wheel.

Either disable the whole plugin or just change those specific actions and it all goes away.

Hope that helps.

Wonderful.  Disabled vpswitch plugin and annoyance is gone.  Not sure how to access the viewport plugin settings... if I could just go in there and disable scroll wheel flipping but not button 2-rotate cube that would be nice.

---

### Post by issih on 2008-08-11
Okay to keep button 2 actions, reenable viewport switcher, then go into its config options (just click on its little icon).

On the "Desktop-based viewport switching" tab make sure "move left" and "move right" are disabled and that initiate plugin action is set to button 2.

That ought to get you what you want :)

---

### Post by overdrank on 2008-08-11
Moved :)

---

