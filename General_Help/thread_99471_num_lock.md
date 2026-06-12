---
title: "num lock"
date: 2005-12-05
forum: General Help
---

### Post by emerick7 on 2005-12-05
Just a quick question... is there a way to set num lock to be activated every time I boot linux?  Not a big deal at all, just wondering if there's a way.  Thanks... ty

---

### Post by soulestream on 2005-12-05
sudo apt-get install numlockx


soule

---

### Post by filipenetto on 2005-12-05
I'm not sure, but, take a look on the **/boot/grub/menu.lst** file. Maybe have an option of 'num lock on'. I'm not on my linux to confirm that, but, try this.

Bye ...

---

### Post by emerick7 on 2005-12-05
didn't find anything in menu.lst, but I tried the install numlockx and this is what I got... any ideas?

> ty@ubuntu:~$ sudo apt-get install numlockx
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package numlockx


I get "Couldn't stat source package list..." when I go to System > Admin > Add Apps as well - I think it might be part of the same problem.  Thanks, Ty

---

