---
title: "upgrade to breeze"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by ehalverson on 2005-12-22
i've been running linux for about 6 years now, but i'm new to ubuntu.  i've searched all over, and i can't find out HOW i'm supposed to upgrade to breeze.  i'm running the version that came out right before it (hoary), i know how to upgrade packages with apt-get and so on, i just can't figure out how to change my overall version to get the upgraded repositories.  do i jsut edit /etc/apt/sources.list to contain the new repositories? only reason i havn't tried that is because i'm afraid that will get me new packages but still use a depricated baselayout.  any help would be appreciated.

edit: well as it turns out i'm an idiot, i just noticed the sticky topic above on how to do this.  maby there should be a link on the main page? and if there already is one, maby it should just be a little more obvious, sorry for wasting everyone's time, feel free to delete this thread.

---

### Post by Irony on 2005-12-22
See this for several options;

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

---

### Post by daschl on 2005-12-22
[QUOTE=ehalverson]i've been running linux for about 6 years now, but i'm new to ubuntu.  i've searched all over, and i can't find out HOW i'm supposed to upgrade to breeze.  i'm running the version that came out right before it (hoary), i know how to upgrade packages with apt-get and so on, i just can't figure out how to change my overall version to get the upgraded repositories.  do i jsut edit /etc/apt/sources.list to contain the new repositories? only reason i havn't tried that is because i'm afraid that will get me new packages but still use a depricated baselayout.  any help would be appreciated.

edit: well as it turns out i'm an idiot, i just noticed the sticky topic above on how to do this.  maby there should be a link on the main page? and if there already is one, maby it should just be a little more obvious, sorry for wasting everyone's time, feel free to delete this thread.[/QUOTE]

just change all "hoary" to "breezy" in the sources.list and then run apt-get update and apt-get dist-upgrade

---

