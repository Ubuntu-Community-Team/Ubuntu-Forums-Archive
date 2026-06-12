---
title: "I dont know own to put different wallpapers on different screen..."
date: 2008-08-25
forum: General Help
---

### Post by TheFate on 2008-08-25
When I put a wallpaper, all my screens takes the same... but I would like to get different one for all of them... can you help me?

Thanks a lot for helping me!:)

---

### Post by Genius314 on 2008-08-25
You can do this if you are running Compiz. (If you're not, look up how to use it)
If you can't run Compiz, there are other ways to get different wallpapers, but none of which are easy.
Also note: If you use Compiz for the wallpapers, you won't be able to use icons.

First, you have to disable the desktop in Nautilus. Press Alt-F2 and type in "gconf-editor" (without the quotes).
Go to apps>nautilus>preferences. Uncheck "Show Desktop." If done right, your desktop background should disappear, including icons. (You may have to log out and back in for it to take effect.) Close the window.

Now, install CCSM, if you haven't already. In a terminal, type:
> sudo apt-get install compizconfig-settings-manager

Go to System>Preferences>CompizConfig Settings Manager. Go to the Wallpaper plugin, and click "New." Put an images path in the box (e.g. "/home/user/Pictures/wallpaper.png"). The other settings don't matter, since you're using an image. Now add a few more.

Switch desktops to see all the different wallpapers. You can rearrange them in CCSM to make them appear on another desktop.

---

### Post by sayakb on 2008-08-25
Try wallpapoz: [http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

---

### Post by Orlsend on 2008-08-27
Can ther be a Way with out killing my desktop. I reall want to kee the Icons

---

