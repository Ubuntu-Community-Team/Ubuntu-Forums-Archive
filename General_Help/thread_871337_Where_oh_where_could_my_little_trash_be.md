---
title: "Where oh where could my little trash be?"
date: 2008-07-26
forum: General Help
---

### Post by Spaceman9 on 2008-07-26
I was using Nautilus in root mode to send three folders I don't need anymore to the trash folder. When I looked in the trash folder there was nothing there. I looked at the trash folder on my second hard drive(which has PCLOS on it) but there wasn't anything in the trash there. I looked in the two trash folders on my backup drive, but there wasn't anything in the trash there either.

Is it possible the folders I sent to trash were deleted and never sent to trash?

Where oh where could my little trash be? How come there aren't little black digital trash bags to keep these things nice and tidy? Thankx for any help.

---

### Post by scragar on 2008-07-26
could be in root's trash, but by far the easiest method is to just use locate to find the trash
```
locate Trash | less
```
using q to exit and arrows to scroll. Once you know the folder to empty(I think it's /root/.local/share/Trash for root) ```
gksu nautilus
``` and delete it from trash to get rid of it forever, or in future remember that shift+delete = delete perminantly

---

### Post by Spaceman9 on 2008-07-26
> **scragar said:**
> could be in root's trash, but by far the easiest method is to just use locate to find the trash
```
locate Trash | less
```
using q to exit and arrows to scroll. Once you know the folder to empty(I think it's /root/.local/share/Trash for root) ```
gksu nautilus
``` and delete it from trash to get rid of it forever, or in future remember that shift+delete = delete perminantly

Thankx for your help. I didn't know there could be so many trash folders. Is all this supposed to be here?

/home/.Trash-0
/home/.Trash-root
/home/bruce/.local/share/Trash
/home/bruce/.local/share/Trash/files
/home/bruce/.local/share/Trash/info
/home/bruce/.mozilla/firefox/wbfqi5qe.default/Cache.Trash
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash/trash.py
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash/trash.pyc
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash/trash.theme
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash/trash_empty.png
/home/bruce/Wallpaper And Sounds/KDE Themes 35/ChristmasTime/CT_Trash/trash_full.png
/root/.local/share/Trash
/usr/lib/bonobo/servers/GNOME_Panel_TrashApplet.server
/usr/share/gnome-2.0/ui/GNOME_Panel_TrashApplet.xml
/usr/share/pixmaps/large/Trash-Empty-192.png
/usr/share/pixmaps/large/Trash-Empty-Accept-192.png
/usr/share/pixmaps/large/Trash-Full-192.png
/usr/share/pixmaps/large/Trashbox-64.png
/usr/share/pixmaps/large/Trashbox.png
/usr/share/pixmaps/other/Trash-Closed.png
/usr/share/pixmaps/other/Trash-Empty-Accept.png
/usr/share/pixmaps/other/Trash-Empty-Accept_North.png
/usr/share/pixmaps/other/Trash-Empty.png
/usr/share/pixmaps/other/Trash-Empty_North.png
/usr/share/pixmaps/other/Trash-Full-Accept_North.png
/usr/share/pixmaps/other/Trash-Full.png
/usr/share/pixmaps/other/Trash-Full_North.png
/usr/share/pixmaps/other/Trash-Open.png
/usr/share/pixmaps/other/Trash-empty.png
/usr/share/pixmaps/other/Trash-full.png
/usr/share/pixmaps/other/TrashFull-Closed.png
/usr/share/pixmaps/other/TrashFull-Open.png
/usr/share/zynaddsubfx/banks/Guitar/0033-Trash Guitar 1.xiz
/usr/share/zynaddsubfx/banks/Guitar/0034-Trash Guitar 2.xiz
/usr/share/zynaddsubfx/banks/Misc/0033-Trash Synth 1.xiz
/usr/share/zynaddsubfx/banks/Misc/0034-Trash Synth 2.xiz
/usr/share/zynaddsubfx/banks/Misc/0035-Trash Synth 3.xiz

---

### Post by cariboo on 2008-07-26
I would suggest looking here:

```
/root/.local/share/Trash
```

for your missing files.

Jim

---

### Post by scragar on 2008-07-26
I'd use ```
gksu nautilus /home/.Trash-root
```
and check there, check /home/.Trash-0 as well, since both of those look like contenders for roots trash.

---

### Post by Spaceman9 on 2008-07-26
Ok, I tried “locate Trash | less” and “/root/.local/share/Trash” and “gksu nautilus /home/.Trash-root“ and everything is empty. I don't know where it went but as long as I don't stumble over it in the dark I suppose it doesn't matter. 

Thankx for your help guys.

---

