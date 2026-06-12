---
title: "What's the difference Between Emerald, Compiz, Widgets"
date: 2008-08-11
forum: General Help
---

### Post by David C on 2008-08-11
Hi all, 

I'm a relatively new linux user (at least to its GUI interface), I'm confused. There seems like a thousand themes for Emerald, Dominos, Plastik etc. 

I don't get it though.

There are widget themes, there are themes and windows managers like kde4-windows-decorator, gtk-windows-decorator etc.

What's Kwin?

Can someone tell me what role does each of them play in a typical system?

I'm extremely confused :-(

---

### Post by rainwalker on 2008-08-12
Gnome and KDE are the two main desktop environments (DE) on Linux. Gnome is the default for Ubuntu, while Kubuntu uses KDE. Gnome is aimed towards usability and simplicity, while KDE is aimed towards looks and customization. They're what give the desktop it's overall layout and method of use.
I don't know much about KDE, but I know Kwin is the name of it's window manager, and the look/feel of everything is controlled by the Qt theme. Metacity is the Gnome window manager, and the look/feel of everything is controlled by the GTK theme. Themes require a theme engine to be used (Murrine themes need the Murrine engine, Aurora themes need the Aurora engine, etc). I'm pretty sure Domino is one of the KDE theme engines. Themes, theme engines, and tons of other stuff can be downloaded from [www.gnome-look.org](www.gnome-look.org) and [www.kde-look.org](www.kde-look.org), obviously depending on which DE you use. KDE apps can run in Gnome, and vice-versa, though they may not fit your overall theme.
Some people prefer Emerald as their window manager, because it's a bit flashier and customizable.
Compiz Fusion is what lets you have all the eyecandy (transparency, animations, etc), created from the merging of Beryl and Compiz (two forked projects that used to provide eyecandy for the Linux world). From Ubuntu 7.10 and onward, it's installed by default. You can enable effects in 8.04 under the Visual Effects tab under System > Preferences > Appearance. To configure all of Compiz's settings, install the package "compizconfig-settings-manager" and it will be under System > Preferences > Advanced Desktop Effects Settings.

---

### Post by Mgiacchetti on 2008-08-12
emerald decorates your windows

compiz adds different effects to the whole ubuntu experience

widgets are things like a clock, calendar, system monitor, etc.

and widget themes are themes for your widgets

---

