---
title: "nVidia drivers"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-15
Okay, so I finally got to desktop in Ubuntu! Woo hoo!

However, I need a little help with my graphics card drivers (eVGA GeForce 6800 GS PCIe), as I'm stuck in 1024x768 and want to be able to go with full resolution (1280x1024 on this monitor). I need some help in updating my drivers to support higher resolution. Can anybody help me out (keeping in mind I'm a total newcomer to linux and not very computer savvy to begin with, so please make the instructions idiot proof)?

Forgive me if this is answered elsewhere. I did a search but either didn't find what I wanted or didn't understand what I found... :-k 

Many thanks in advance.

---

### Post by renzokuken on 2006-02-15
i beleive this might help

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest)

---

### Post by Coelocanth on 2006-02-15
Aye, I saw that thread. Being new, I need to ask: how do I ensure I have both Universe and Multiverse repositories enabled?

---

### Post by Coelocanth on 2006-02-15
Okay, I think I figured out how to enable the repositories. However, when opening Synaptic I get this:

W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Anyone know what this means and how to fix it?

---

### Post by renzokuken on 2006-02-16
open up a console and type (making sure synaptic is closed)

# sudo apt-get update

then open synaptic again and see what happens.......

if that doesnt work, then copy and paste the contents of /etc/apt/sources.list and we'll have a look just to double check its all correct

---

