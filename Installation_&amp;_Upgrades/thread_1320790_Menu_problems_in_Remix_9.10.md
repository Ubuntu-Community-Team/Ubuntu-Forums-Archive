---
title: "Menu problems in Remix 9.10"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by ohiomoto on 2009-11-09
I recently upgraded 2 laptops to 9.10.  Everything went smooth, but there is an issue with the way the menu items are displayed on one of them.  For example, I added a new menu item "Trunk" to the "Folders" menu, but the menu didn't expand.  This resulted in the "Volumes" menu being written over top of my "Desktop" menu item.  
[ATTACH]135497[/ATTACH]

Also, my Systems>Administration menu is not showing all of the menu items.  The items are on the menu as I am sometimes able to find them with the pointer even though I can't see them.  The are just below the viewable area, but I cannot scroll down any further.  I suspect that the items have spilled out of the menu panel as my my "Desktop" folder did, but I'm only able to scroll down far enough to show last row of the panel.  Removing menu items does not solve the problem.
[ATTACH]135498[/ATTACH]

I have removed and reinstalled the netbook remix packages without success.  Any ideas?

**_EDIT: Workaround added!!_**

> **ohiomoto said:**
> Okay, I stumbled upon a workaround when I added Startup Manager to my computer.  It added an icon to the Systems>Administration menu and in the process, expanded the panel that holds the menu items.  Now it works as it should.  

It looks like the problem is that the panel doesn't always correctly calculate the number or rows.  To test this, I added a few extra folders to my Files & Folders menu and it also worked.  So we can "fix" the problems by adding (or subtracting) menu items as needed.

If your Files & Folders menu has a faulty display, simply open a File Browser and drag some folders to the lower half of the "Places" menu in the side pane.  Or you could remove folders if you like. This should work for any of the menus.

---

### Post by karimruan on 2009-11-09
What is your screen resolution set to? Have you installed all the drivers for your video card?

---

### Post by ohiomoto on 2009-11-09
1280x800, NVIDIA GeForce 8400M GS card.  I have tried activating both available drivers and there is no difference.

---

### Post by ohiomoto on 2009-11-09
Interesting...If I use 1024x768, the menus work as they should.  There seems to be an issue with 9.10 at 1280x800.  9.04 worked fine on this machine.

Any ideas?

---

### Post by karimruan on 2009-11-12
Well, i suggest keeping your resolution there, it should look better, and if it works.... MAybe try submitting it as a bug?

---

### Post by ohiomoto on 2009-11-12
The bug has been reported and confirmed on Launchpad. No solution yet.

---

### Post by dedavai on 2009-11-30
Experiencing the same problem on Lenovo S12.

---

### Post by ohiomoto on 2009-12-05
Okay, I stumbled upon a workaround when I added Startup Manager to my computer.  It added an icon to the Systems>Administration menu and in the process, expanded the panel that holds the menu items.  Now it works as it should.  

It looks like the problem is that the panel doesn't always correctly calculate the number or rows.  To test this, I added a few extra folders to my Files & Folders menu and it also worked.  So we can "fix" the problems by adding (or subtracting) menu items as needed.

If your Files & Folders menu has a faulty display, simply open a File Browser and drag some folders to the lower half of the "Places" menu in the side pane.  Or you could remove folders if you like. This should work for any of the menus.

---

### Post by carlomag on 2009-12-05
I was waiting for a workaround to solve this issue.
But, sorry for that, I don't understand your kind suggestion.
I use UNR 9.10 in italian language, so I can't find exactly what you mean.
Please, could you describe in a more specific and redundant way what I have to do?
Thank you.
Carlomag

---

### Post by ohiomoto on 2009-12-05
**_For the Files & Folders menu:_**  Open up a file browser and add or remove folders to the the lower part of the "Places" menu in the side pane as shown below.  This will change the "Files & Folders" menu.
[ATTACH]138723[/ATTACH][ATTACH]138719[/ATTACH]

**_For the Systems menu:_**  Open Systems > Preferences > Main Menu.  Select Administration and adjust the number or menu items until you achieve the proper results.
[ATTACH]138725[/ATTACH][ATTACH]138720[/ATTACH]

---

### Post by carlomag on 2009-12-06
Ah, OK; I've understood and I thank you so much!

But, now is clear to me that the main problem is the icons' dimension.
In my very small screen (eeepc 701) icons are definitely too big; so, only a few of them are enaugh to occupie all the areas of the menus.

Well: I need a way to change icons' dimension and a way to change the room of the branches of the menu.

Humm,... thinking to try somewhat different from UNR.

---

### Post by Planker on 2009-12-21
I'm having a similar problem with my menus, except that only my Games menu appears incorrectly (see attachment). The names of the icons in the last row flows offscreen and I can't scroll down further to see them. The two workarounds posted above don't seem to apply here. So, I'm wondering if anyone knows how I can fix this.

---

### Post by erlguta on 2010-01-08
Is anyone working on this bug?. I'm surprised that there is no solution yet, given the gravity of this very annoying bug, which throws into question the usability of an entire project (UNR). And for Canonical allowing to release a product so poorly done. This are a series of details that never would be done by Google with its Chrome OS or Intel with its Moblin.

---

### Post by VMbuseck on 2010-01-22
I just installed UNR 9.10 and had the same problems. The netbook-launcher appears with overlapped icons. Some of them are not reachable, because other icons are covering this icons completely.
I disabled all UNR features and use a "normal" gnome desktop, until this bugs get fixed:

Greetings Michael :(

---

### Post by erlguta on 2010-02-07
> **_For the Systems menu:_**  Open Systems > Preferences > Main Menu.  Select Administration and adjust the number or menu items until you achieve the proper results.
[ATTACH]138725[/ATTACH][ATTACH]138720[/ATTACH]

Ohiomoto the problem is that i dont want to delete items in system -> administration. I want that appears all the default items...

---

### Post by erlguta on 2010-02-07
Wow!. I think i soved it.
I had installed 'htop' program that put another section 'System tools' in the lateral menu. So i edited the menu and disable the programs in the 'system menu'...in this case only 'htop' program and Voila!...now all my icons looks fine in System -> Administration

---

### Post by horstmacin on 2010-02-22
I found another workaround for this issue. I solved the problem with the  overlapping icons by reducing the font size from 10 to 8.

---

