---
title: "*Panic* Upgrade to breezy failed, can't get wifi dongle started"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2005-12-23
I tried to upgrade my hoardy version to Breezy using a tutorial somewhere. He said to change the apt-get sources to the one from breezy. And apt-get update everything. Ok I did that but he got stuck on gettext. so I reainstalled gettext and (stupid me) rebooted my machine cause he just continued doing the other upgrades. Now he gives a kernel-panic when booting on the new kernel.
When I select my old kernel everything "works" but I can't get my wifidongle started. The module is loaded .. but the alias isn't in the list when I type iwconfig... is there anyway to fix this ? Can I just remove the bad kernel ?

---

### Post by az on 2005-12-23
Boot into recovery mode with the working kernel and run

apt-get -f install

It may tell you to run dpkg --configure -a  - Do it.


That should fix everything.


If it does not, you can reinstall the borked linux-image package:

apt-get install --reinstall linux-image-2.6.12-10-386 (or whatever version)

You probably interrupted it while it was making it's initrd or something.

---

