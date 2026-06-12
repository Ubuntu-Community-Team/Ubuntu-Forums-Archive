---
title: "Minimil program launcher?"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Sivan on 2009-05-04
I just re-installed Jaunty as as I was having some odd issues with Firefox. Now I cannot remember how I was able to create a menu system with several programs I use really frequently. This was a very minimal menu system in which I was able to add applications I use all the time. It looks very similar to one application on the task tray, but when you right-click on the icon, you can select properties and then add more applications.

Does anyone have an idea of what this menu launcher might be called?

I've added an file that shows what the program listing looked like.

Thanks

---

### Post by Sivan on 2009-05-04
Anyone have an idea what this menu launcher might be called?

I wish I had made a note of it before I re-installed.

---

### Post by kerry_s on 2009-05-04
sounds like you was using a drawer, right click the panel and add the drawer.

---

### Post by Sivan on 2009-05-04
> **kerry_s said:**
> sounds like you was using a drawer, right click the panel and add the drawer.

Nope, the drawer does not allow you to add applications such as Firefox to it.

---

### Post by kerry_s on 2009-05-05
> **Sivan said:**
> Nope, the drawer does not allow you to add applications such as Firefox to it.

what! thats a new one on me, if i remember right you can drag & drop from the menu right on the drawer, after that you can move it were you want inside the drawer. i'll check after my nephew finishes his homework on it.

okay, i had no problem putting anything, i even can put the panel applets.

---

### Post by mcduck on 2009-05-05
> **Sivan said:**
> Nope, the drawer does not allow you to add applications such as Firefox to it.

Yes, it does. Anything you can put in the panel you can also put in a drawer.

One more option is to create a new menu category for your custom menu, and then add  that menu into the panel:

1. Use the Menu editor (right-click on the Applications-menu -> Edit Menus) to create a new menu category (in addition to the default Accessories, Games, Graphics etc.)

2. Add all the program launchers you want into that menu category.

3. Open the menu, browse into that category. right-click and select "Entire menu"/"Add this as menu to panel".

You'll end with a single-icon panel object that, when clicked, will show all the programs you have added into that menu category. The icon for the applet is changed by changing the icon assigned for the menu category in the Menu editor.

(You can of course use the same right-click + "Entire Menu"/"Add this as drawer/menu to panel" -method to add any of your default menu categories into the panel as menus or drawers)

---

### Post by kerry_s on 2009-05-05
> **mcduck said:**
> Yes, it does. Anything you can put in the panel you can also put in a drawer.

One more option is to create a new menu category for your custom menu, and then add  that menu into the panel:

1. Use the Menu editor (right-click on the Applications-menu -> Edit Menus) to create a new menu category (in addition to the default Accessories, Games, Graphics etc.)

2. Add all the program launchers you want into that menu category.

3. Open the menu, browse into that category. right-click and select "Entire menu"/"Add this as menu to panel".

You'll end with a single-icon panel object that, when clicked, will show all the programs you have added into that menu category. The icon for the applet is changed by changing the icon assigned for the menu category in the Menu editor.

(You can of course use the same right-click + "Entire Menu"/"Add this as drawer/menu to panel" -method to add any of your default menu categories into the panel as menus or drawers)

good 1, i forgot all about that method, haven't seen it in along time. 
it would be more like his pic, 
hold on i'll do some pics.

---

### Post by kerry_s on 2009-05-05
here's what it looks like.

---

