---
title: "Apt-get is trying to remove everything"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Absynthe on 2009-04-10
Yesterday apt-get noticed me that there were 22 upgradable packets; the problem is that among these packets there are some like ksystemlog, kdebase-plasma, kgrubeditor, kdebluetooth, gwenview, kubuntu-desktop, dolphin, kdesudo, adept, konsole, akregator, ark, systemsettings, konqueror, ktorrent, dragonplayer, kde-window-manager, kdepasswd, kmix and many many other, all marked "remove". I never requested such an operation, why is apt-get trying to do so? Synaptic brings up an even longer list of packets marked for removal. Also, I tried to uncheck the "remove" option and to check "upgrade" instead (since most of the packets it's trying to remove are actually upgradable), but it won't let me do it for more than one packet. If I try to change another packet, the previous one goes back to being marked for removal. Why is this happening? How can I solve this problem? Help is very much appreciated since I'm pretty much clueless right now.

---

### Post by joao82 on 2009-04-10
Did you try to install something new before that started to happen? Or to remove some core kde application?
sometimes that happens to me when I play around with replacing installed programs/libraries from the repositories with new ones from websites.

---

