---
title: "Compiz wallpapers"
date: 2008-08-28
forum: General Help
---

### Post by lynx_hanan on 2008-08-28
I want to ask a simple question

can i use a different wallpaper for each desktop in compiz, e-q if i have four desktops can i apply a different wall on each of em and see the effect when i rotate the cube?? if so can anyone tell how

---

### Post by tuxxy on 2008-08-28
> To have different wallpapers for each desktop, follow these steps:

I. Disable "show desktop" in Nautilus
1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

II. Install Compiz Fusion
1. In Terminal, input the following:
Code:
sudo aptitude install compizconfig-settings-manager
2. Exit Terminal

III. Select your desktop wallpaper
1. System --> Preferences --> Advanced Desktop Settings
2. Tick "Desktop Cube" and opt to disable desktop wall if prompted
3. Tick "Rotate Cube"
4. Select "Desktop Cube"
5. Click "Appearance" tab
6. Click "Add" under the "Background Images" field
7. Browse for your desired wallpaper(s), ordering them based on which face of the cube you want them to appear

[http://ubuntuforums.org/showthread.php?t=17359](http://ubuntuforums.org/showthread.php?t=17359)

---

### Post by lynx_hanan on 2008-08-28
Cool it works, just needed to the gconf-editor step

---

### Post by tuxxy on 2008-08-28
Good stuff, now you can mark the thread solved :)

---

### Post by lynx_hanan on 2008-08-28
Its wotking all riteee

But now i cant see my Desktop icons or folders

They are there if browse to the Desktop

can this be fixed

---

