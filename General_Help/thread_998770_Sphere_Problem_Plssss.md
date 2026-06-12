---
title: "Sphere Problem Plssss"
date: 2008-12-01
forum: General Help
---

### Post by Mapras10 on 2008-12-01
Hello everybode i try to turn the cube to sphere bz i like it to much this effect with earth..but i cant to put 4 diferent wallpapers on my 4 desktops so i get error sphere...why i dont have the choise backround images here(picture1) and how can i resolve it..?? thnxxx (sorry 4 my english) something like this [http://www.youtube.com/watch?v=FHQD2p9AG5c](http://www.youtube.com/watch?v=FHQD2p9AG5c)

---

### Post by Forlong on 2008-12-01
You can use the wallpaper plugin to set different wallpapers.

But you'll have to abandon your desktop icons for that:
```
gconftool-2 -s -t b /apps/nautilus/preferences/show_desktop false
```

---

### Post by Mapras10 on 2008-12-01
OMG!!! now my right mouse button is dead and i dont have at all sphere..............

and nothing chanceee in cube -appearence - i cant see again backround images

---

### Post by Forlong on 2008-12-01
> **Mapras10 said:**
> OMG!!! now my right mouse button is dead
Only on the desktop.
If you want to get it back, run this:
```
gconftool-2 -s -t b /apps/nautilus/preferences/show_desktop true
```
then log out and in again. But then you won't get different wallpapers, of course.
> **Mapras10 said:**
> and nothing chanceee in cube -appearence - i cant see again backround images
Like I said, you'd have to configure that in the **Wallpaper** plugin.

---

