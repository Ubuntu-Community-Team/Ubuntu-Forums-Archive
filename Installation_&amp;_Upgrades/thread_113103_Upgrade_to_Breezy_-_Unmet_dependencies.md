---
title: "Upgrade to Breezy - Unmet dependencies"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by LadyLuck on 2006-01-05
Hi all, I've been having some problems upgrading to Breezy, but I beleive I'm getting somewhere (i.e. getting stuck in a new place). The error message is displayed after running:
 
 sudo apt-get update
 sudo apt-get dist-upgrade

 Reading package lists... Done
 Building dependency tree... Done
 You might want to run `apt-get -f install' to correct these.
 The following packages have unmet dependencies:
 libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is    installed
 E: Unmet dependencies. Try using -f.

Befor I run apt-get install with the -f switch I thought I'd try to find out what the error message means.
thanks in advance 
LL

---

### Post by Zelut on 2006-01-05
Its just saying that the package libc6-i686 depends on libc6 v2.3.2.ds1-20ubuntu14 but currently you have 2.3.5-1ubuntu12 installed.  The -f will correct the issue and install / remove packages that are causing problems.

I have never run into problems when using -f install.

---

### Post by LadyLuck on 2006-01-06
Ok thank you! It worked like a charm. The only outstanding problem now is that my keyboard layout is US english although the "keyboard preferences" (System =>Preferences => Keyboard) claims it is Icelandic.
cheers
Bjarni

---

