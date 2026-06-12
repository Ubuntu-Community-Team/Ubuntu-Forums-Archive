---
title: "Cleanup Residual Config Files"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by deejross on 2009-05-20
I'm trying to clean up residual files in /etc from packages that I've already removed. I found this thread: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

But that tells you how to do it from Synaptic....I need to know how to do it from the command line....thanks.

---

### Post by adam@home on 2009-05-20
sudo apt-get autoremove
sudo apt-get autoclean

In synaptic look for DebOrphan and GTK Orphan install them and access the GTK version from the system menu and also use Locale-Purge (install from synaptic too) to remove unused languages

---

### Post by deejross on 2009-05-21
The problem is that I am not running a GUI at all....it's the server edition, so in I need to know how to do it without Synaptic.

I don't think I've made myself clear...I'm looking to clean unused config files, NOT packages. I've already removed the unneeded packages, now I want to clean out their associated config files.

---

