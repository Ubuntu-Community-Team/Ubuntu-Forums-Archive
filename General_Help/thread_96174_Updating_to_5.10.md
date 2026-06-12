---
title: "Updating to 5.10"
date: 2005-11-28
forum: General Help
---

### Post by foo_DK on 2005-11-28
Hi all

I am a fairly new user off Ubuntu, and I am currently using 5.04.

My Question is now, if it is possible to update to Breezy Badger in a easy an painless way, without having to download the entire release..

\\foo`

---

### Post by magnusbb on 2005-11-28
It is very simple, just go edit your /etc/apt/sources.list and replace all mentions of "hoary" in the adresses with "breezy".

Then run "sudo apt-get dist-upgrade", and watch it download and upgrade.

But for some, it can be a pain. If you have a fairly default setup, then things should work, but if you have done much changes to the system by replacing some parts, for example, things can go bad. 

Generally a fresh install is better than an upgrade - this goes for every OS. But in most cases, the dist-upgrade work perfect. My advice would be to make a backup of your system first. There is a great howto in the HOWTO forums for this.

---

### Post by foo_DK on 2005-11-28
well when you say it like that it sounds so easy... :)

I havent got any lines in my sources.list  that countains hoary, and i can't seem to edit the file at all...

---

### Post by joselin on 2005-11-28
You must edit your sources.list as root. Type de following:

$ sudo gedit /etc/apt/sources.list

And then, update the sources and upgrade:

$ sudo apt-get update
$ sudo apt-get dist-upgrade

Regards.

---

### Post by frodon on 2005-11-28
I advice to follow these instructions, all is in the link : [https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

---

