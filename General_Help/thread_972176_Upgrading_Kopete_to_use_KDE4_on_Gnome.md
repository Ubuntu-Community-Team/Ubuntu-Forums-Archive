---
title: "Upgrading Kopete to use KDE4 on Gnome"
date: 2008-11-05
forum: General Help
---

### Post by MunkyJunky on 2008-11-05
I'm currently running Kopete on my Gnome desktop, and when I click 'help > about kopete' it says it's using KDE 3.5.10, and I'd like to upgrade it to be using KDE4 libraries. In Synaptic, I have both 'kopete' and 'kopete-kde4' packages installed. I'm also running the Amarok-nightly package, which is using KDE 4.1.69. I'd like to get Kopete up to the same level, so I can remove the older KDE libs. 

Solutions, anyone? I'd also greatly appreciate a solution that DOESN'T flood my applications menu in KDE programs.

---

### Post by Jorge_C on 2008-11-06
Hi,

If you have "kopete-kde4" installed you should be able to remove "kopete" and launch the one using qt4 with this command
```
/usr/lib/kde4/bin/kopete
```
You can create a launcher or add it to your menu.
By the way, in my menu the actual command used to launch it is this
```
/usr/lib/kde4/bin/kopete -caption "%c" %u
```
I don't know what the options mean, and both with and without them seems to work fine for me using gnome, too.

---

