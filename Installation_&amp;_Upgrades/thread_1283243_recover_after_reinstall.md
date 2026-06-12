---
title: "recover after reinstall"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by amitch88 on 2009-10-05
i am using ubuntu 9.04 on my dell laptop with dual boot ubuntu and vista,
we can download exe files on windows and then use it on anywhere.
but whenever i reinstall ubuntu i must download all software.
how can i download ony packages which can i copy in my pendrive and can install in other place and can use them after reinstall on ubuntu like exe files

---

### Post by mac9416 on 2009-10-05
All the .deb (Ubuntu's software packages) files APT donwloads to install are kept in /var/cache/apt/archives (until you run "sudo apt-get clean"). You can copy them onto a flash drive, then after a reinstall of Ubuntu, copy them right back into /var/cache/apt/archives. APT won't download them again, just use them straight out of that folder.

---

