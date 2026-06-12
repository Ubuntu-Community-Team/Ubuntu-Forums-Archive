---
title: "Missing menu links in system--&gt;administration"
date: 2008-07-13
forum: General Help
---

### Post by Duranxl on 2008-07-13
Hi all.

Suddenly my system->administration has 50% of the menu links.
E.g. software sources has totally disappeared.
I tried adding them with the code but they wont work

Any help:confused:

thanks

---

### Post by Nexusx6 on 2008-07-13
Have you un-installed anything via apt-get? Even something that might seem completely un-related?

---

### Post by Duranxl on 2008-07-13
> **Nexusx6 said:**
> Have you un-installed anything via apt-get? Even something that might seem completely un-related?

Ye nvidia drivers, maybe some other stuff..

---

### Post by jonlemur on 2008-07-13
Try right clicking on the System button, and select "Edit Menus"  On the left there should be a list where you can select System->Administration at the bottom.  Select that and see if there are any unchecked boxes, and check them if you want them in the list.

---

### Post by CatKiller on 2008-07-13
Have you removed yourself from the admin group, perhaps? Removing the ability to use *sudo* will also remove the entries that require elevated permissions to run from the menu.

---

### Post by Duranxl on 2008-07-13
> **jonlemur said:**
> Try right clicking on the System button, and select "Edit Menus"  On the left there should be a list where you can select System->Administration at the bottom.  Select that and see if there are any unchecked boxes, and check them if you want them in the list.

Im sorry, i should have added this in my first post.
Yes this is the first thing i checked, but none of the links (like software sources) appear in the checkbox list.


> **CatKiller said:**
> Have you removed yourself from the admin group, perhaps? Removing the ability to use *sudo* will also remove the entries that require elevated permissions to run from the menu.

Well i log in as root..?

---

### Post by CatKiller on 2008-07-13
> **Duranxl said:**
> Well i log in as root..?

Well... that is a bad thing to do.

I don't know if that would affect the menu.

---

### Post by Duranxl on 2008-07-13
> **CatKiller said:**
> Well... that is a bad thing to do.

I don't know if that would affect the menu.
Should i just use my own account with admin rights and then use SUDO?

---

### Post by CatKiller on 2008-07-13
> **Duranxl said:**
> Should i just use my own account with admin rights and then use SUDO?

That is the sensible way to do it, and it's possible that things might assume that to be the case, since that is the default setup and deviation from that is strongly discouraged, and so might behave peculiarly. I don't know for sure that that is the case, but it's a feasible scenario.

A number of security problems are prevented by running as a regular user. If you need to do system-wide things, then you have the power to do so for a short period. Nothing can get affected system-wide without you being aware of it.

The home folder is still vulnerable, since all users are able to write to their home folder, but since that's where all of your settings and data are kept, that is what you'd be backing up anyway.

---

