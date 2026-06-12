---
title: "google earth fonts, what the?"
date: 2008-10-22
forum: General Help
---

### Post by phoenix_snake on 2008-10-22
alright so I installed google earth on ubuntu some time back, oh yeah sorry I can't provide screenshots of the problem right now, its the latest version though.

google earth looks like windows 98 on ubuntu, and the fonts are so small, its impossible to read them, anyone else with this problem?

is there a fix?

---

### Post by Vadi on 2008-10-22
Google Earth uses Qt 4 (unlike gtk+ for other programs in ubuntu), hence why the desktop integration is rather crappy.

Install the qt config tool: [click]("apt:qt4-qtconfig"), and go to system - preferences - qt 4 settings and tinker with the fonts there.

---

### Post by phoenix_snake on 2008-10-22
thanks, I will try this later

---

### Post by phoenix_snake on 2008-11-03
just tried it after a long time....lol, it doesn't work?

---

### Post by phoenix_snake on 2008-11-04
bump

---

### Post by philinux on 2008-11-04
gedit ~/.config/Google/GoogleEarthPlus.conf

I've amended the render section to look like this.
```
[Render]
CompassVisible=true
FeetMiles=false
GuiFontFamily=Arial Black
GuiFontSize=12
GuiFontStyle=0
IconSize=2
```

It's not perfect but it's an improvement. I've got msttcorefonts installed. If anybody got a better solution give it up.

---

### Post by phoenix_snake on 2008-11-04
> **philinux said:**
> gedit ~/.config/Google/GoogleEarthPlus.conf

I've amended the render section to look like this.
```
[Render]
CompassVisible=true
FeetMiles=false
GuiFontFamily=Arial Black
GuiFontSize=12
GuiFontStyle=0
IconSize=2
```

It's not perfect but it's an improvement. I've got msttcorefonts installed. If anybody got a better solution give it up.
thanks it worked, I am just suspicious here, is google earth for linux the windows version with a few hacks or something?

---

### Post by Vadi on 2008-11-04
No, it uses the Qt toolkit ([http://www.kdedevelopers.org/node/2098](http://www.kdedevelopers.org/node/2098)). Which has pretty poor Gnome integration, hence why it looks quite out of place.

---

### Post by phoenix_snake on 2008-11-04
> **Vadi said:**
> No, it uses the Qt toolkit ([http://www.kdedevelopers.org/node/2098](http://www.kdedevelopers.org/node/2098)). Which has pretty poor Gnome integration, hence why it looks quite out of place.
lol oh sorry I had forgot the top part of my thread you replied to :p

any plans for better integration?

---

### Post by philinux on 2008-11-04
I've raised a bug. Please feel free to add any comments.
[https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/293628](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/293628)

Also if you use tools options choose 3d fonts it does not work. And clicking restore defaults introduces what look like the correct lines in ~/.config/Google/GoogleEarthPlus.conf but again this is ignored.

---

### Post by Vadi on 2008-11-04
> **phoenix_snake said:**
> lol oh sorry I had forgot the top part of my thread you replied to :p

any plans for better integration?

No idea. I don't work at Google or Trolltech (Qt people) and haven't heard any news about this.

---

