---
title: "[SOLVED] Nice sharp power-manager icon"
date: 2008-09-09
forum: General Help
---

### Post by robz0rz on 2008-09-09
Hey


The power manager icon in my notification area is awful... I've got icons for nice and sharp 24x24 or 22x22 versions of the icons, but for some reason, all I get is some sort of scaled down version of a bigger icon, which means the icon ends up being blurry and ugly as it is now.

I've found the icons for the gnome-power-manager at /usr/share/gnome-power-manager/icons/hicolor/[sizes]/status


How can I make the gnome-power-manager use the sharp icons that are located there instead of what it's using now?


I've attached a full screenshot, a cut-out to show what exactly I'm talking about, and a GIMPed version of how it should look. Thanks for your time

---

### Post by robz0rz on 2008-09-10
I've managed to solve it myself. What I had to do is remove all the gpm-related icons from my own icon-theme and then delete the icon cache. It now looks nice and sharp :D

---

### Post by ulogo on 2008-09-10
> **robz0rz said:**
> I've managed to solve it myself. What I had to do is remove all the gpm-related icons from my own icon-theme and then delete the icon cache. It now looks nice and sharp :D

Will you able to post your icon here so that we have the clear idea of it. I am a logo designer and want to learn new things always.

---

### Post by robz0rz on 2008-09-10
It's not my icon, it's the standard gpm icon. I just wanted my notification area to display the correct sized one. You have these icons yourself, they are situated at /usr/share/gnome-power-manager/icons/hicolor

---

