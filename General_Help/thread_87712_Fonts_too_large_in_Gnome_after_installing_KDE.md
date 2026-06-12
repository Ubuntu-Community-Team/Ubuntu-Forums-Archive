---
title: "Fonts too large in Gnome after installing KDE"
date: 2005-11-08
forum: General Help
---

### Post by shandar on 2005-11-08
Hi!

I wanted to try out KDE yesterday and decided to install the kubuntu-dektop and kde-artwork packages. All went well and KDE works as it should although I don't like it :-) The problem is when I log in to Gnome again, the fonts in all GTK apps are shown at an ugly size 14 while I've set them to be size 8. I've checked the Fonts settings and they're set correctly, yet nothing happens when I change the font and size. I tried to set all fonts to size 20, but nada! Any ideas?

---

### Post by ogregore on 2005-11-08
Shandar,

I had a similar problem and also experienced it when I was using SuSE 9.2.

Check the GTK settings in KDE's preferences, I think I had to tell it to use the GTK settings in KDE (using the same Gnome theme I was using) and all my fonts returned to normal in Gnome.

Hope this helps.

Ogre

---

### Post by eyebrowman92 on 2005-11-08
this is my own opinion, but, i think kde is horrible. it is way too slow and is made for morons, no offense. i like xfce and gnome way mor than i do kde. xfce4 is super fast and is also better than gnome, i think.

---

### Post by WorLord on 2005-11-09
Its the gtk2-engines-gtk-qt package.  It kind of takes over, even when not in a KDE environment.  

You should set the KDE defaults to use GTK to draw GTK apps, and then get rid of this package.

---

