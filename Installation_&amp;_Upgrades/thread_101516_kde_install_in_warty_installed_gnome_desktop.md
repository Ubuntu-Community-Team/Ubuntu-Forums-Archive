---
title: "kde install in warty installed gnome desktop"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2005-12-10
i tried to install kde in my ubuntu desktop warty installed version of ubuntu
although session button shows kde in the menu i am not able to invoke kde
the synaptic and apt-get sys kde is installed and newest version.
how can i make it work
some configuration file is holding on to gnome desktop
somebody please show some light
thanks
:KS :KS :KS

---

### Post by aysiu on 2005-12-10
KDE?

Try ```
sudo apt-get install kubuntu-desktop
``` and see if that makes a difference.

Or maybe upgrade to Hoary or Breezy...

---

### Post by ramaswamyps on 2005-12-10
Segmentation fault
now i remebered while installation dpkg returned error code 2 and asked me to run dpkg-reconfigure -a
in thet i must have goofe something up in the base cofiguration.
i reinstalled from the warty instaler and again tried to install kde and now it works and i am now upgrading packages.

the segmentation fault came in in the old installation when trid the suggested 
apt-get install kubuntu-desktop
now in the new installation it seems working ok
some problems with fde control center windows.
i am not able to see ok apply reset buttons at the bottom of the windows in the setup windows.
i tried all 3 possible screen esolutions still same.

what i shoud adjust to get the full wondow of control center??

:confused: :confused: :confused:

---

### Post by aysiu on 2005-12-10
[QUOTE=ramaswamyps]Segmentation fault
now i remebered while installation dpkg returned error code 2 and asked me to run dpkg-reconfigure -a
in thet i must have goofe something up in the base cofiguration.
i reinstalled from the warty instaler and again tried to install kde and now it works and i am now upgrading packages.

the segmentation fault came in in the old installation when trid the suggested 
apt-get install kubuntu-desktop
now in the new installation it seems working ok[/quote] In other words... it's working now?

> 
some problems with fde control center windows.
i am not able to see ok apply reset buttons at the bottom of the windows in the setup windows.
i tried all 3 possible screen esolutions still same.

what i shoud adjust to get the full wondow of control center??

:confused: :confused: :confused: [http://www.kubuntuforums.net/forums/index.php?topic=445.0](http://www.kubuntuforums.net/forums/index.php?topic=445.0) may help

---

