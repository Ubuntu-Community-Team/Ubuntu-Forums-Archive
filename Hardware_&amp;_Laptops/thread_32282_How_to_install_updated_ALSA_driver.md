---
title: "How to install updated ALSA driver?"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by Donshyoku on 2005-05-06
I am using an Intel Azalia chipset for my sound, and I am told that it only works with the latest development release of ALSA.

Now, I don't know how to install much besides a .deb, .rpm, or apt format.  So tarballs  and source are out of the question at my current skill level.

How can I go about getting and installing the latest ALSA driver the easiest?

Thanks in advance! ;-)

---

### Post by ludi on 2005-05-06
[QUOTE=Donshyoku]I am using an Intel Azalia chipset for my sound, and I am told that it only works with the latest development release of ALSA.

Now, I don't know how to install much besides a .deb, .rpm, or apt format.  So tarballs  and source are out of the question at my current skill level.

How can I go about getting and installing the latest ALSA driver the easiest?

Thanks in advance! ;-)[/QUOTE]
You don't have to be scared about software compilation. I can say you really are in "good hands" with Ubuntu. Well, someday you'll have to use it.
Debs package system is easer than anyone.
Take a look at Ubuntu wiki about software management. [http://www.ubuntulinux.org/wiki/FrontPage](http://www.ubuntulinux.org/wiki/FrontPage)
This is a little how-to  about synaptic: [http://www.ubuntulinux.org/wiki/SynapticHowto](http://www.ubuntulinux.org/wiki/SynapticHowto)
The most things you need are in the Wiki, so just do a simple search and you will find it.
The Ubunutu have the best (my opinion) package management system (apt), and you won't have problems to deal it.
PS: I think that there isn't binary package of the last version. So, grab the last source from alsa project and make the thing happen :)
You'll need build-essential and the kernel-header that match with the current kernel version of your system.
Follow the README and INSTALL file and everything will be fine.

---

