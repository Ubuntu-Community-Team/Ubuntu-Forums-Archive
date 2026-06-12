---
title: "problem to upgrade from 8.04 to 8.10"
date: 2008-11-22
forum: General Help
---

### Post by rduijkeren on 2008-11-22
Hi,

I followed the upgrade process, in software sources check normal releases (update). In the update manager do the update check, it says "Your system is up to date The package information was last updated less than one hour ago"but I don't get the upgrade possibility of 8.10. Tried it also with a CD (8.10) but no way I get 8.10 on my system. 

What to do?

---

### Post by adult swim on 2008-11-22
push alt+f2 and run ```
update-manager -d
```

---

### Post by rduijkeren on 2008-11-22
didn't work I saw in a second downloading files and then I got your system is up to date. I did another check but still the same. It looks like there are files downloaded but not installed. I also did a restart...

---

### Post by adult swim on 2008-11-22
you dont have the upgrade option at the top of the box like this?

---

### Post by rduijkeren on 2008-11-22
no, and I did the upgarde with my VM machine and that worked perfect. So I think one of former downloads did go wrong. Is there a forced upgrade possibility?

---

### Post by TeXtonyx on 2008-11-22
I think changing hardy to intrepid may work, in sources.lst making
a backup file of sources.lst (sources.lst.bak) first.

cd /etc/apt

gksudo gedit sources.lst

Replace all occurrences of hardy with intrepid and save the file.

apt-get update

apt-get dist-upgrade

I've tested this method with Debian analogues, so it should work unless 
something fundamental is already broken.

---

### Post by rduijkeren on 2008-11-22
Thnx, mate,

It took a long time to install but I've 8.10...

Again thnx...:)

---

### Post by rduijkeren on 2008-11-24
I still have the problem I had with 8.04 namely that the update manager doesn't update. It counts the downloaded files but doesn't install them. Is there a possibility to reset that?

---

