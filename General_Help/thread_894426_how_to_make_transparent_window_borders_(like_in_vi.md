---
title: "how to make transparent window borders (like in vista)"
date: 2008-08-19
forum: General Help
---

### Post by syms on 2008-08-19
hi,
im still playing with my new pc :) . so how to to do that? currently by default window decorations are transculent only when window is inactive. i searched in compiz settings but didnt found anythink.

---

### Post by CheeseEatingBulldog on 2008-08-19
This is really easy, 

* Go to the "advanced desktop effects settings" under system --> preferences.
* Go to the "General Tab" (at the top) and select the "Opacity" tab (all the way on the right).
* In the "Window opacity" field add some window names by clicking new --> for example to have the drop down / pop up menus slightly transparent add "dropdownmenu" and "popupmenu" and set an opacity level for each.

This should result in your main menus and pop up menus being transparent. You can add different window types there to make more things transparent.

---

### Post by syms on 2008-08-19
i know that, so what command is for decorations?

---

### Post by pjones0404 on 2008-08-19
you may need to install emerald and then set it as your windows decoration. 

after you install emerald go to compiz settings manager. then go to window decoration and put " emerald --replace" in the command field. you may need to restart x at this point to load emerald. 

once this is done then you can go to gnome-look.org and look for emerald themes or some are called beryl themes. Most of these themes are translucent and look a lot better than the standard metacity themes.

---

### Post by billgoldberg on 2008-08-19
Take a look at the link in my signature about customizing Ubuntu.

You'll find it usefull.

---

### Post by karasuman on 2008-08-19
I recommend installing and using Emerald.  I know it sounds daunting, but it's actually very easy.

To install Emerald, open up a terminal and type:

```
sudo apt-get install emerald
```

Type in your password, etc.

Once it's installed, you should find it under System -> Preferences -> Emerald Theme Manager.

When you open the ETM, you'll see two sets of tabs.  On top, keep it on "Themes Settings."  If you have any themes installed, you'll see them listed under "Themes" on the lower set of tabs.  (If you're looking for themes, try gnome-look.org, and I've attached one that I made.  You can access it by unzipping the download and choosing "Import" on this screen.)  Use the "Edit Themes" tab to customize your theme.  Most of the transparency settings will be under the first of the new options, "Frame Engine."  I recommend vrunner or truglass, despite the fact that Oxygen mentions Vista.  :)

---

### Post by binbash on 2008-08-19
install emerald-theme-manager

---

### Post by syms on 2008-08-20
thanks guys and girls for info :D

---

