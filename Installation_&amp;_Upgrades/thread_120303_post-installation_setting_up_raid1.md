---
title: "post-installation: setting up raid1"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by mtlife on 2006-01-21
How can I setup raid1 AFTER installation? All the howto's and tutorials i can find say that i must make my raid -config in the installation process. My config is now:

8 gig ubuntu drive (hdb)
40 gig drive - unused (hdc)
80 gig drive - unused (hdd)

And know I want to have the 40 gig drive in a raid1 array with a 40 gig partition on hdd. And maybe, even the 8-gig in an array also on hdd in raid1. But i dont know if that is possible, I know it is possible to make the first array. Can anyone help me out?

---

### Post by lha on 2006-01-21
[QUOTE=mtlife]How can I setup raid1 AFTER installation? All the howto's and tutorials i can find say that i must make my raid -config in the installation process. My config is now:

8 gig ubuntu drive (hdb)
40 gig drive - unused (hdc)
80 gig drive - unused (hdd)

And know I want to have the 40 gig drive in a raid1 array with a 40 gig partition on hdd. And maybe, even the 8-gig in an array also on hdd in raid1. But i dont know if that is possible, I know it is possible to make the first array. Can anyone help me out?[/QUOTE]

It's possible. You already have the documentation that tells you how to do this. :) Mdadm comes with /usr/share/doc/mdadm/rootraiddoc.97.html. It is quite good. You'll be interested in "Part II. RAID using initrd and grub", starting from section 3. The same document is also available [online.]("http://alioth.debian.org/download.php/668/rootraiddoc.97.html") [http://juerd.nl/site.plp/debianraid]("http://juerd.nl/site.plp/debianraid") and [http://deb.riseup.net/storage/software-raid/]("http://deb.riseup.net/storage/software-raid/") have also some instructions, but they lack some useful information found in rootraiddoc.97.

---

