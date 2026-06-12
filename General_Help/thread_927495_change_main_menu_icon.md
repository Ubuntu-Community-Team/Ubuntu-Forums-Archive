---
title: "change main menu icon?"
date: 2008-09-23
forum: General Help
---

### Post by drudogg on 2008-09-23
i have applied a theme that i like, but not the icon for teh main menu...

can somebody tell me how to get a different one. an ubuntu symbol, 3d or something...

hardy heron...

---

### Post by renzokuken on 2008-09-23
the icons you install are actually stored in ```
/home/*username*/.icons
```

go into the appropriate folder for your icon theme and try and find **distributor-logo.png** or whatever the name of your current start icon is. simply replace this icon with your desired icon.

e.g.

```
*# backup/move/rename original icon*

mv distributor-logo.png distributor-logo-backup.png

*# then replace with your custom icon*

mv my-custom-icon.png distributor-logo.png
```

EDIT: the actual name/location of the start icon tends to change from theme to theme but should be fairly obvious which one it is.

---

### Post by yragrelluf on 2008-09-23
pick the new icon you want (should be on desktop) and open a terminal and type sudo mv /home/yourname/Desktop/whatevericon /usr/share/themes/whatevertheme/scaleable/places and press enter. this will replace the distributor icon with your custom icon. reboot and you will be all set! Just make sure your custom icon is named start-here.png

---

### Post by yragrelluf on 2008-09-23
downloaded themes are in the hidden icons folder in home, but if you want them permanently, move them into /usr/share/themes

---

### Post by drudogg on 2008-09-23
i swapped the file, but it did not change... logout and login did not effect it.

---

### Post by nkri on 2008-09-23
I had a pretty tough time doing this a while back, but managed to get it to work.  You have to scale whatever picture you want to use to fit each size in the theme (in my case, it was 8x8, 12x12, 16x16, 22x22, 24x24, 32x32, 48x48, scalable) using GIMP.  You then have to replace them with 
```
sudo mv *custom_icon* /usr/share/icons/*icon_theme*/*size*
```

Then, restart the panel (or reboot, I can't remember which...if one doesn't work, try the other):
```
killall gnome-panel
```

You may want to try the same process (replacing each size of icon) with the icons in your home folder instead of /usr/share/icons.  In this case, do not use sudo when replacing or you will not have regular privileges to the files.

Good luck!
-nkri

---

### Post by drudogg on 2008-09-24
i replaced teh on  in the scalable folder... maybe i just did not get teh right one.. oh well no real biggie.

---

### Post by Genius314 on 2008-09-24
> **drudogg said:**
> i replaced teh on  in the scalable folder... maybe i just did not get teh right one.. oh well no real biggie.

If your panel is a common height (like 48x48, 24x24, etc), then you should replace the icon in that folder (e.g. /48x48, not /scalable).

---

