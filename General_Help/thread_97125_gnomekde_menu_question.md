---
title: "gnome/kde menu question"
date: 2005-11-30
forum: General Help
---

### Post by woodb on 2005-11-30
Hey all,

Sorry if this has already been answered, I didn't find it if it has.

Is there a way to install KDE and keep the KDE menu items out of gnome (and vice versa)?  

Thanks in advance,
woodb

---

### Post by Xian on 2005-11-30
I don't like or use KDE, but there are some commands that might help you out some with the Gnome Menu. Of course you could I suppose just use the Gnome Menu Editor and remove the KDE entries assuming they won't respawn.

```
$ cd /usr/share/applications/kde
$ sudo chmod a+rw /usr/share/applications/kde/*
$ for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
$ sudo chmod 644 /usr/share/applications/kde/*
```

---

### Post by Sutekh on 2005-11-30
[QUOTE=Xian]I don't like or use KDE, but there are some commands that might help you out some with the Gnome Menu. Of course you could I suppose just use the Gnome Menu Editor and remove the KDE entries assuming they won't respawn.[/QUOTE]

That actually does work, they don't respawn.  I tried using that method, becuase there were some KDE apps I wanted in GNOME.

But that script is great for getting rid of them all, and is a lot easier than deselecting each one.

---

### Post by Xian on 2005-11-30
Okay, great Sutekh. I wasn't sure.

---

