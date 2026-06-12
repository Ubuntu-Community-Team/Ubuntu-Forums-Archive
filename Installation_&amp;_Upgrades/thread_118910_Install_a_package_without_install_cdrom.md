---
title: "Install a package without install cdrom"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by wwbach on 2006-01-18
I'm using apt-get to install a package that is evidently on the base install cdrom:

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

Is there a way to force apt-get to download a package that is part of the install cd?  I need to add a package to a remote machine and there is no cdrom on site and no way to burn one.

Thanks.  -- Bud

---

### Post by kaamos on 2006-01-18
Yes, you can comment out the cd from the installation sources. Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```
Add a # to the start of the line that has the cd, save the file and do
```
sudo apt-get update
```
And you are good to go.

Hope this helps.

---

### Post by wwbach on 2006-01-18
Thanks!  That was blindingly obvious.  I had looked in sources.list but somehow missed the very first line which referenced the cdrom.  Thanks again.  -- Bud

---

