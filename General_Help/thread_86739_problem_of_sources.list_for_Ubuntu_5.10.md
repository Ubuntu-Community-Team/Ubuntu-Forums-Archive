---
title: "problem of sources.list for Ubuntu 5.10"
date: 2005-11-06
forum: General Help
---

### Post by Paul Chang on 2005-11-06
Just installed Ubuntu 5.10 (i386 version) on a machine with AMD64 (I first installed Ubuntu AMD64 version, but it freezes the machine. So I have to remove it and reinstalled i386 version). Everything works fine except for source package list. When I tried to update the source list, I got the messages that "Couldn't stat source package list" -- as shown in the following:
----------------------------------------------------------------------------------------------
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
-----------------------------------------------------------------------

Could anyone kindly let me know what wrong with it? 

Thanks a lot

---

### Post by Arktis on 2005-11-06
Breezy backports aren't up yet, so you should just leave them commented out for now.

---

### Post by PuleX on 2005-11-06
Just check the backports project page sometimes: 

> Ubuntu Backports is split into many distributions and sections. Currently, these are:

   1. warty-backports -- Stable, tested updated packages for Ubuntu Warty (4.10)
   2. warty-extras -- Stable, tested add-on packages for Ubuntu Warty (4.10). Example: FreeNX
   3. hoary-backports -- Stable, tested updated packages for Ubuntu Hoary (5.04)
   4. hoary-extras -- Stable, tested add-ons for Ubuntu Hoary 

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by Paul Chang on 2005-11-06
Thanks for the information. Didn't notice that before.

---

