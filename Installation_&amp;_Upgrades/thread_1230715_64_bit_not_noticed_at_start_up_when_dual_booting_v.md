---
title: "64 bit not noticed at start up when dual booting via the wubi windows install method"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by cgb223 on 2009-08-03
installed 64 bit Ubuntu on 64 bit windows and after seemingly flawless installation, on restart it doesnt give option to select Ubuntu at windows boot manager (boots like windows is the only one installed) then when i tried to uninstall it, it gave me an error and led me to a folder that didnt exist, decided to make it show hidden folders and now computer has no icons, programs or anything... had to reinstall windows. so can i get help with the ubuntu parts, and could Ubuntu have caused the vista blow up? (probably not... we all know how much vista is a "wonderful" operating system to work with...)

---

### Post by running_rabbit07 on 2009-08-03
> **cgb223 said:**
> installed 64 bit Ubuntu on 64 bit windows and after seemingly flawless installation, on restart it doesnt give option to select Ubuntu at windows boot manager (boots like windows is the only one installed) then when i tried to uninstall it, it gave me an error and led me to a folder that didnt exist, decided to make it show hidden folders and now computer has no icons, programs or anything... had to reinstall windows. so can i get help with the ubuntu parts, and could Ubuntu have caused the vista blow up? (probably not... we all know how much vista is a "wonderful" operating system to work with...)

There have been a lot of complaints about Ubuntu not working via Wubi with Vista.

I would recommend after you have finished your reinstall of Vista that you use the Device manager Tools and shrink the NTFS partition by about 10-15 Gigs and install Ubuntu into a new partition.Don't forget to defragment before altering your partition.

*Edit: retracted the Partitioner warning. Please see the site listed in Sef's post.*

Let us know if you need help installing Ubuntu via partition.

---

### Post by Sef on 2009-08-03
> ** WARNING-** Do** NOT** use Ubuntu Partitioner to shrink a Vista partition. There have been many complaints about Vista not recognizing the partition.

You can use it, but you need to follow theses directions from [GParted's FAQ #9]("http://gparted.sourceforge.net/faq.php").

---

### Post by cgb223 on 2009-08-04
Thanks I'm familiar with the gparted live disks. Just wanted to know if the wubi thing was fixable. It's working fine now. Need sleep though... Lol

---

