---
title: "[SOLVED] squished font problem"
date: 2008-09-22
forum: General Help
---

### Post by elli222 on 2008-09-22
I seem to have a squished fonts problem.

This appears to be related to the msttcorefonts package, but it appears only partially related however.

When i run xmms, it behaves as expected, when i install the ms font package, i get them all squished

While as image magick, the same used to apply, but now it is always squished.

This may apply to other applications aswell

see attached images...

[ATTACH]86109[/ATTACH]

[ATTACH]86110[/ATTACH]

any help would be greatly appreciated...

---

### Post by elli222 on 2008-09-22
bump :(

---

### Post by elli222 on 2008-09-22
i really cannot begin to comprehend this problem...

Its REALLY strange. Ill try making a new xorg.conf with the nvidia settings thingie (and uninstall msttcorefonts

---

### Post by benerivo on 2008-09-22
What effect does altering the System>Preferences>Appearances>Fonts settings have on this problem? You might also try```
sudo dpkg-reconfigure fontconfig-config
```(remember the default settings it displays as you may want to set them back to default. Then do```
sudo dpkg-reconfigure fontconfig
```and log out/back in.

---

### Post by elli222 on 2008-09-23
alright, ive managed to fix one problem, my resolution wasnt really the right one for my screen, that knocks out the tiff interface (imagemagick- at least i think its tiff (less or more :P)

But the xmms and msttcorefonts problem proceeds

The sys>pref>font has no effect on it whatsoever, ill try reinstalling the msttcorefonts package and seing if my res fix changed anything

EDIT: Resolution fixed it...

---

### Post by elli222 on 2008-09-23
Ok, SOLVED! but how can i install new fonts?

---

### Post by Yooglee on 2008-09-23
thanks for help

---

