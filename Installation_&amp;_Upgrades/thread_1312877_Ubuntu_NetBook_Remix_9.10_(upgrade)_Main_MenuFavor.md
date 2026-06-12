---
title: "Ubuntu NetBook Remix 9.10 (upgrade) Main Menu/Favorites Workaround"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ohiomoto on 2009-11-03
After upgrading my UNR install to 9.10 my system had two "favorites" menu items.  The top one had some default applications and a few of the applications that were in my original favorites folder.  The lower favorites was left with a few applications that I had made custom launchers for.  I tried to use the main menu editor, but the the top level folder wasn't there and I couldn't hide the lower level folder.  After a little fooling around, I found the solution.

First of all the new favorites folder is not contained in the Main Menu list.  You can add launchers to it by right clicking them and then adding them to your favorites folder.  This means that you need to have the applications launchers defined in some other menu before adding them to the new favorites menu. This this works fine, but you can not reorder them in the Main Menu editor. They simply show up in the order they were added, so you could remove and add launchers to achieve a desired order.  (I'm sure there is config file somewhere, but I haven't dug into the issue that far.) 

Now about that pesky second favorites menu. You simply need to remove/hide/uncheck any remaining launchers from that menu.  Once the items are removed, you can hide the folder and it will no longer appear on the desktop.  Keep in mind that if you simply add the launchers to the new favorites folder, you will not be able to edit them from the Main Menu editor. I recommend adding the launchers to an appropriate folder first (i.e., Programming, Games, Office, etc.).  You can add them to your new favorites folder later.

I suspect the only those of us who created custom application launchers in our old favorites folder are affected because all of the other launcher were move to the new folder during upgrade.  I don't think it's really a bug.  It seems to be a minor difference in how the folder is handled in 9.10.

I hope this helps.

[ATTACH]134539[/ATTACH]

---

### Post by LoSt180 on 2009-11-03
I found where the favorites are hidden. Go to your home folder and show hidden files. Navigate to ~/.gconf/apps/netbook-launcher/favorites/ 
There is a %gconf.xml file, open it in gedit, and you can reorder the entries. 

I'm not sure how to edit the icons of the launchers like in the menu list, but I did notice that for everything you add to favorites (ie., clicking the little plus sign), it creates an entry in ~/.local/share/applications/ and that xml file links back to there.

Hopefully we can dig deeper into the "new" netbook launcher.


After some additional digging, you can right-click the .desktop file (in the folder above) select properties and customize the icon from there.

More experimenting: you can change the order around by editing the values in gconf-editor instead of fudging around the xml file.

---

### Post by ohiomoto on 2009-11-03
Good stuff LoST180.

I also found a work around for the gray background in the indicator-applet-session. I changed the Background settings in the Panel Properties to Solid Color.  Then by adjusting the transparency level I could replicate the original look of the panel. It would be nice to change the font color of the indicator-applet-session, but I'll live with it the way it is until there is an update.

[ATTACH]134614[/ATTACH][ATTACH]134615[/ATTACH]

---

### Post by Herdnerfer on 2009-11-04
Great stuff here, appreciate the effort. I have a question you might be able to answer. I have a lot of bookmark links in my favorites folder, which does add a folder to the favorites folder, but doesn't seem to place a .desktop file in the other folder. I really want to change that default web icon to a custom icon for each site. If there is anything you can do to help i would appreciate it. Thank you.

---

### Post by franciscocosta on 2009-11-05
> **Herdnerfer said:**
> Great stuff here, appreciate the effort. I have a question you might be able to answer. I have a lot of bookmark links in my favorites folder, which does add a folder to the favorites folder, but doesn't seem to place a .desktop file in the other folder. I really want to change that default web icon to a custom icon for each site. If there is anything you can do to help i would appreciate it. Thank you.

I have the same problem.. I would also like to know how to reorder the icons!

---

### Post by Perturbed Penguin on 2009-11-22
Nothing on changing icons? I would also love to know if there is a way to adjust icon settings in the favorites folder.

---

### Post by ohiomoto on 2009-11-23
No fix for the menu yet.  See Lost180's post below for info on the reordering the icons.  I haven't messed with it yet myself.

> **LoSt180 said:**
> I found where the favorites are hidden. Go to your home folder and show hidden files. Navigate to ~/.gconf/apps/netbook-launcher/favorites/ 
There is a %gconf.xml file, open it in gedit, and you can reorder the entries. 

I'm not sure how to edit the icons of the launchers like in the menu list, but I did notice that for everything you add to favorites (ie., clicking the little plus sign), it creates an entry in ~/.local/share/applications/ and that xml file links back to there.

Hopefully we can dig deeper into the "new" netbook launcher.


After some additional digging, you can right-click the .desktop file (in the folder above) select properties and customize the icon from there.

More experimenting: you can change the order around by editing the values in gconf-editor instead of fudging around the xml file.

---

### Post by DeanFX on 2009-11-30
In netbook remix 9.10 I right clicked the panel on the top so I can change it from solid color to image but the panel properties arent there? 

May be a nub question, but where can I change the panel color and all on this?

---

### Post by mrcevic on 2009-12-01
I dont know if this is the appropiate thread but the topic I need to report is related: after upgrading to Ubuntu Netbook Remix 9.10 the indicator session for a non admin user is NOT displaying (tried the background workaround but it doesn't work because it's simply not showing up). Has someone experienced the same problem? I see the indicator session as admin but not as a SIMPLE user. Please help if you can

---

### Post by Perturbed Penguin on 2009-12-03
Turns out it is not a noob question DeanFX. lol If you look closely there is a very small, like one pixel, dot on the bar. On mine I think it was to the left of the notification area originally(volume, wifi, etc). I found out through sheer accident that if you remove the indicator-applet-session, clock and notification area all on the right side of the bar then the pixel-dot will move all the way over to the right side of the bar. Once it is located here you can right-click in the very top-right-corner of the screen and get the usual preferences menu. JUST BE SURE NOT TO CLOSE THE 'add to panel' WINDOW UNTIL YOU HAVE RE-ADDED EVERYTHING YOU WANT, otherwise you will simply have to do it all over again. I was testing using external monitors and it screwed up the positioning of all my icons and such up there and thats how I ended up discovering this, lol. Hope you can figure it out!

---

### Post by Perturbed Penguin on 2009-12-03
...Not sure but what I just posted may be able to help you as well mrcevic - perhaps if you try re-adding it to the menubar or something? I hope I am understanding you right in that the 'indicater-applet-session' thing isn't showing at all whenever you boot as a normal user?

---

### Post by ohiomoto on 2009-12-04
Check this topic out: [http://ubuntuforums.org/showthread.php?t=1345974](http://ubuntuforums.org/showthread.php?t=1345974)  

It shows in detail how to get access to the panel.  The same principles apply to both sides of the panel.  In a nut shell, the panel is hidden behind all the different applets it holds.  You need to move them around to access the panel itself.

---

### Post by Perturbed Penguin on 2009-12-07
Thats great, a much better way of accessing apps/properties than what I have done! Great link! ;)

---

