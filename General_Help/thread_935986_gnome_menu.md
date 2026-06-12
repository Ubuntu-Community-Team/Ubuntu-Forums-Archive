---
title: "gnome menu"
date: 2008-10-02
forum: General Help
---

### Post by trappleye on 2008-10-02
I recently installed mythbuntu on my desktop. I have been running Ubuntu for about a year now, and decided I wanted to turn my desktop into a PVR (tivo for desktop). I started with a fresh install, and it seems like I have a mixture of gnome and X. I don't have the standard gnome menus, I have xfce menus, and I can't drag launchers from the menu onto the panel like I could in ubuntu. I'm also missing the 'system' and 'places' menus. It also doesn't automatically mount my external hard drives or my second internal hard drive. 
[IMG]http://i30.photobucket.com/albums/c342/trappleye/MyScreenshot3.jpg[/IMG]

---

### Post by davidryder on 2008-10-02
You can install gnome and when you logout change the session to gnome.

```
sudo apt-get install gnome
```

MythTV will still work, you'll just have your gnome back.

---

### Post by trappleye on 2008-10-02
Well the apt-get didn't work because I already had it installed. The relogin solved it. Mythbuntu skips the login on bootup, and I hadn't thought to change my session.

---

