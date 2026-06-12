---
title: "[SOLVED] Bottom panel Trash icon not working properly"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by jrz on 2008-12-17
Ubuntu 8.10 Fresh install on a new Compaq notebook using the alternate CD.
Note: The same CD was used to install on another Compaq notebook which does not have this problem, and the same options were used during both installations.

Problem: After the install, an "Empty Trash" icon appears at the far right of the lower panel. Some audio, video, and text files were moved to the Desktop from another system running ubuntu 7.04, and were later removed by right clicking on them selecting "Move to trash". At a later time I noticed the icon still displayed empty, and pointing at the icon a notice appears stating "No items in Trash". Left clicking the Trash icon opens Nautilus 2.24.1, which displays all the files which were moved to the Trash. Right clicking the icon displays the options and "Empty Trash" is enabled and does allow me to empty the trash. 
Also, when looking at Nautilus, it is displaying a "Full Trash" icon when there are files in the trash, and an "Empty Trash" icon when there is nothing in the trash.
The Trash is found in ~/.local/share/Trash/Files which Nautilus displays, but the panel icon does not appear to be properly associated with the same path. Perhaps there is a configuration file some where? I've looked and googled to no avail.
I've also tried rebooting, changing themes, icon themes, also to no avail.

---

### Post by luoenzhen on 2008-12-18
try to delete some file again and empty the trash to see if it works.

---

### Post by jrz on 2008-12-18
I wish it were that simple, we've been using the system over a week now and have deleted files and emptied the trash numerous times each day. It appears that Nautilus and Gnome are not associated with the same trash location, but we have been unable to find where that association is set.

---

### Post by aheckler on 2008-12-18
Try resetting your panel:

```
killall gnome-panel
```

---

### Post by jrz on 2008-12-19
No positive effect, besides wouldn't this occur each time the system is rebooted?
It appears the icon is not associated with the correct path to the trash when pointed at with the mouse as it pops up a small window stating "No items in Trash" when ~/.local/share/Trash/files does have content. Both left clicking the icon or right clicking the icon and selecting "open" result in opening a Nautilus GUI which displays the files in the trash, AND the icon displayed by Nautilus is a Trash-full icon and changes to a Trash empty icon when the trash is emptied. There must be a piece of code somewhere which operates on the panel icon testing the trash directory for content that determines which icon to display, but I've been unable to find where it exists.
Even more important, I would like to determine WHY this problem occurred with a clean install on a new system as it is something that should not occur at  all, and is a BUG which seems to have roots as far back as 2005, as seen from googling on it.

---

### Post by aheckler on 2008-12-19
I "caught" this particular bug at one time as well. From what I can remember, it had something to do with the trash folder tha Ubuntu creates on removable media (flash drives, etc). So maybe if you plug them in, delete their trash folders (which are hidden by default), and fiddle about a bit more the icon will go back to working as normal.

---

### Post by jrz on 2008-12-19
I've given that thought also as I use 3 Kingston memory sticks for moving files between systems, but I don't ever delete files on external devices, and use cut and paste ONLY. But just as a precaution I checked each one of them to see if they contained any hidden or trash files and they are all empty.
You don't happen to know what piece of code determines which icon to display do you? I may be wrong, but I'm led to believe the bottom panel trash icon operates under Gnome, and Nautilus determines the icon display independently. The problem doesn't exist on my other system using ubuntu 7.04, but 7.04 uses ~/.Trash instead of ~/.local/share/Trash/files and I've even tried creating a ~/Trash directory and putting some files in it to see if that would cause an icon change, which it did not. It would really be nice to be able to look at the code that controls this function, if I knew what and where it was.

---

### Post by aheckler on 2008-12-19
Sadly I don't know. I'm not a programmer haha

---

### Post by jrz on 2008-12-19
I finally resolved the problem and below is the post I made at [https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/72468](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/72468)

I seem to have stumbled across the cause AND solution to my icon problem. After applying the current recommended updates I had to reboot the system, and at the login screen I decided to look and see if the Options at login had changed from 7.04 ubuntu. Under Sessions I was offered to use the previous session or change to another. Although I assumed that I had been using Gnome, I selected Gnome anyway, and was then asked if I wished to make the change permanent as I had previously been using Xclient. I was unaware I had been using Xclient and had not been given a choice previously to select it, but once the Desktop came up I immediately noticed the Trash icon was showing full, and is now displaying how many items are contained in the trash when I point to it.
In my case this problem is now cleared, and perhaps some others may benefit from what I found?

---

