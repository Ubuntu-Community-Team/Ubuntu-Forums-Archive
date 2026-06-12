---
title: "[SOLVED] Panel position"
date: 2008-09-10
forum: General Help
---

### Post by MadMac on 2008-09-10
Howdy!

What I have done is placed both panels at the bottom of the screen.  The problem is that every time I reboot/restart one winds up back at the top of the screen, so I have to play the move-n-move again game to get both back to the bottom of the screen.  What I would like to know is if there is a way to make *both* stay at the bottom of the screen at all times?

I am using Ubuntu Hardy, 8.04.

Thanks!

---

### Post by MadMac on 2008-09-12
*Bump*

---

### Post by fragos on 2008-09-12
This is an intelligent guess which I haven't tried. Try Configuration Editor -- apps-> panel -> default_setup-> toplevels-> top_panel-> orientation. Try changing it from top to bottom.

---

### Post by Frogbarf on 2008-09-12
My fresh installation of Hardy doesn't have configuration editor in the menus, and I'd guess neither does the OP's machine, so here's how to set it up:

**Right** click *"Applications"* in the menu bar. Then click *"Edit Menus"*. A dialog box pops up headed *"Main Menu"*. Under the first main heading, *"Applications"* there's an entry *"System Tools"*; click that. You'll now see a list of system tools, including configuration editor; just click that to turn on a check mark in the box beside it, then click "close" in the lower right corner of the dialog box.

---

### Post by MadMac on 2008-09-19
> **fragos said:**
> This is an intelligent guess which I haven't tried. Try Configuration Editor -- apps-> panel -> default_setup-> toplevels-> top_panel-> orientation. Try changing it from top to bottom.

Thank you, kind one, that did most of the trick!    :mrgreen:

I found that, when the box -> disable_movement <- is checked both of the panels remain where they are placed.

Thanks again!

---

