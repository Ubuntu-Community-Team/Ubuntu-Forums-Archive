---
title: "Can't update Gnome-Do"
date: 2008-07-30
forum: General Help
---

### Post by cszikszoy on 2008-07-30
Hello,

I seem to have a strange problem.  I'm trying to update gnome-do from 0.4.0.21 to the latest 0.5.97.  I follow the information on the wiki (here: [https://wiki.ubuntu.com/GnomeDo/Installation](https://wiki.ubuntu.com/GnomeDo/Installation)).

After clearing the old folders, updating software sources list, and typing
```
sodu aptitude install gnome-do
```It installs the old version of Do (0.4.021 I think this is the version thats in the official ubuntu repository) and not the old one.

I can go to synaptic, search for do, and in the version, it shows 0.5.97, but when I install it from there, it still brings up the old version of gnome-do!

The only way I got around this was finding an actual deb for the new version somewhere, and installing it there.

If anyone has any idea about this strange behavior it would be greatly appreciated.

Thanks,
-Chris

---

### Post by Mgiacchetti on 2008-07-30
how about checking your settings in synaptic?

---

### Post by cszikszoy on 2008-07-30
checking which setting?

---

### Post by invenit on 2008-07-30
Looks like a bug to me, cszikszoy.

I loaded Gnome do after I read some favorable comments in the forums at Donationcoder this week.

I also encountered the same bug when I attempted to upgrade. I got around it by rekeying the site's instructions after a couple of minutes install of an earlier drive image.

Anyway, it works great now. (Still testing the plugins, however.)

---

