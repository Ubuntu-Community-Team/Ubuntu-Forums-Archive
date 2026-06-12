---
title: "Custom loading screen?"
date: 2005-11-27
forum: General Help
---

### Post by eatnumber1 on 2005-11-27
Is it possible to change the ubuntu loading screen?

Also, is it possible to add a shutdown screen instead of showing the text?

---

### Post by smgil on 2005-11-27
You can install gnome-splashscreen-manager.

---

### Post by 0okami on 2005-11-27
[QUOTE=smgil]You can install gnome-splashscreen-manager.[/QUOTE]

and then go to [http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=bf0e8b889b6decd93ef069e21997e008](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=bf0e8b889b6decd93ef069e21997e008)


[QUOTE=eatnumber1]Is it possible to change the ubuntu loading screen?
Also, is it possible to add a shutdown screen instead of showing the text?[/QUOTE]

(usplash screen pherhaps? - the one that shows items loading like: modules - ok | blah - ok  )
That one im not too sure yet... but it is possible to change. Im waiting on a good how-to.

---

### Post by Insane on 2005-11-27
How do you install it? I cant find it in synaptic....

---

### Post by Xian on 2005-11-27
[QUOTE=Insane]How do you install it? I cant find it in synaptic....[/QUOTE]

It's in the Universe repos.
You can also use gtweakui.

```
apt-cache policy gnome-splashscreen-manager
gnome-splashscreen-manager:
  Installed: (none)
  Candidate: 0.2-1ubuntu1
  Version table:
     0.2-1ubuntu1 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

---

### Post by Xian on 2005-11-27
[QUOTE=eatnumber1]Also, is it possible to add a shutdown screen instead of showing the text?[/QUOTE]
For this you would need to use a bootsplash, or something like [Upower](http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1).

---

### Post by Insane on 2005-11-27
I cant find that universe repos ctegory or anythign similar.

Now, i have resorted to search all the packages, but there is no gnome-splash or anything similar.

Is there a setting that will display these things....maybe...I sound so stupid.

---

### Post by Xian on 2005-11-27
[QUOTE=Insane]I cant find that universe repos ctegory or anythign similar.[/QUOTE]
From the wiki: [How To Enable Universe Repos](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse).

---

### Post by Insane on 2005-11-27
Thanks!

---

