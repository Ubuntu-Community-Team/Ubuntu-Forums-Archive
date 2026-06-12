---
title: "Compiz messing up window edge"
date: 2008-08-27
forum: General Help
---

### Post by alex199020 on 2008-08-27
When i have compiz fusion enabled so i can have the cube and such the bar across the top of my windows (the one with expand, close, minimize on) disappears and i cant move the windows around the screen. If i go into appearance and set visual effects to non it sorts it all out. 
I had a little play with the compiz settings but can't seem to sort the problem. Which option/plug in in compiz is responsible for this sort of thing.
Thanks in advance.

---

### Post by alex199020 on 2008-08-28
Anyone? :(

---

### Post by tuxxy on 2008-08-28
Install emerald theme manager to manage the compiz window theme which is dissapearing

```
sudo apt-get install emerald
```

Launch emerald from **system > prefs > emerald** and now when the borders dissapear select a theme in emerald to use, if they dont re-apper then select your emerald theme and type this into terminal

```
emerald --replace
```

You could add the that command to your sessions to prevent you needing to run it at every login.

If you need some themes [download from here ]("http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=102")

---

