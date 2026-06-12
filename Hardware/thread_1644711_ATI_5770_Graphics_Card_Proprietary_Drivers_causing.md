---
title: "ATI 5770 Graphics Card Proprietary Drivers causing issues"
date: 2010-12-13
forum: Hardware
---

### Post by akand074 on 2010-12-13
Hey guys,

So I just built a new system (specs in my signature). And everything is fine until I activate my proprietary drivers all the panels turn grey and ugly (imaged attached). Anyone have a similar issue/know how to fix it? Any help would be greatly appreciated.

---

### Post by ajgreeny on 2010-12-13
They don't look grey and ugly to me, but then they look just like mine, and i like mine.

This may just be the choice of theme you have, which looks like Ambiance.  What do you think the panels should look like?  Why not play around with customize, in the theme dialog, and see if a different "controls" choice, added to what you have looks better to you.

---

### Post by akand074 on 2010-12-13
> **ajgreeny said:**
> They don't look grey and ugly to me, but then they look just like mine, and i like mine.

This may just be the choice of theme you have, which looks like Ambiance.  What do you think the panels should look like?  Why not play around with customize, in the theme dialog, and see if a different "controls" choice, added to what you have looks better to you.

If you look at the top and bottom panels.. they are grey, no matter what theme I choose. I just want the Ubuntu default.. it was fine right before installing the proprietary drivers.

---

### Post by akand074 on 2010-12-13
I just attached a picture of my desktop with the drivers uninstalled. Everything is pretty much perfect, the theme is right, selected items are the default (orange), where as when the proprietary drivers are installed they are grey with blue selected items and there is nothing I can do to change it. I've noticed when the drivers are installed:

- Panels go grey/selected items are blue only in panels
- Icons completely change
- A system beep comes out of my speakers every time I click almost anything
- Changing themes, alters only the window border nothing else

Why would activating the graphics card even cause system beeps to start?

EDIT:
Running 
```
sudo killall gnome-settings-daemon
``````
sudo gnome-settings-daemon
```Fixed the panels.. now some aspects of my system is using one theme.. while the others are still using that other grey/blue theme.. I'm getting error messages about gnome-settings-daemon when I go to Appearances.. getting closer to a solution. Though it goes right back to it's normal grey/blue state after a restart.

Running this next fixes the rest of the issues:

```
rm -vr ~/.gconf/apps/nautilus && killall nautilus
```

Temporary fix though.. I have to run those commands on startup every time.

---

### Post by ajgreeny on 2010-12-14
Oh!, I see what you mean.

However, I have no way to try to duplicate this problem, as my system still uses only open source drivers, and I choose to have a light grey panel, anyway; I find it easier on the eye.

Could be compiz is implicated in some way?

---

### Post by akand074 on 2010-12-14
> **ajgreeny said:**
> Oh!, I see what you mean.

However, I have no way to try to duplicate this problem, as my system still uses only open source drivers, and I choose to have a light grey panel, anyway; I find it easier on the eye.

Could be compiz is implicated in some way?

No I don't believe so. I had been looking researching it and found the bug page for it. Seems everybody having the problem had an "/" installed on the SSD and "/home" on an HDD. Apparently the SSD loads way too fast so they load before the configuration files from the HDD. For most people putting a 2 second wait on starting gnome-settings-daemon solved their issue. It didn't for me though. Another thing to mention is that for most people, it seemed to happen in 10.10 but not in 10.04.

I may look up a more permanent fix in the future, but perhaps this will fix on it's own after updates and stuff. Also 11.04 might not have the issue, especially since they are dropping gnome-shell.

EDIT: I'd just like to add just FYI that ever since I switched my boot to a text based boot instead of a graphical boot (changing "quiet splash" to "text" in grub), and starting X/gdm manually the problem has not come back.

---

