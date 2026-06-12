---
title: "installing update for ubuntu 8.04?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Vexe on 2009-06-29
so im kinda new but been playing around with ubuntu!
 iv upgraded to 9.10 but reverted to 8.04 because all of 
my setting were working like desktop effects and what not,
but now when i try to check for updates it tells me this and wondering
if someone can help me with this problem===>>


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.  

release 8.04(hardy
kernel linux 2.6.24-24-generic
gnome 2.22.3

this says something about adding cd-rom but it works fine just kinda stumped! the only reason i care is because i wake up eveymorning and says to update but err! thanks again_cheers
 (\ /)
 (o.0)
 (> <)

---

### Post by raymondh on 2009-06-30
> **Vexe said:**
> so im kinda new but been playing around with ubuntu!
 iv upgraded to 9.10 but reverted to 8.04 because all of 
my setting were working like desktop effects and what not,
but now when i try to check for updates it tells me this and wondering
if someone can help me with this problem===>>


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.  

release 8.04(hardy
kernel linux 2.6.24-24-generic
gnome 2.22.3

this says something about adding cd-rom but it works fine just kinda stumped! the only reason i care is because i wake up eveymorning and says to update but err! thanks again_cheers
 (\ /)
 (o.0)
 (> <)


Hello Vexe,

If you go to your software sources (system > admin) and un-tick the CD ROM box .. you should be OK.

to check after,

```
sudo apt-get update
sudo apt-get upgrade
```

If you wish to upgrade to the new kernel ...

```
sudo apt-get dist-upgrade
```

Happy Ubuntu-ing.

---

