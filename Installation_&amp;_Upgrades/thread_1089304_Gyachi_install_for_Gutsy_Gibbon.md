---
title: "Gyachi install for Gutsy Gibbon"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by jeff_flynn on 2009-03-07
Halp! I don't know how to install Gyachi for Ubuntu 7.10 Gutsy Gibbon

---

### Post by ve4cib on 2009-03-07
I would assume you download the appropriate .deb packages from here:

[http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)

Then either double-click on them to install them or open a terminal, change to the directory you saved them in, and execute

$ sudo dpkg -i *.deb

---

### Post by martrn on 2009-03-07
1. Goto [http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575]("http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575")

2. type:  ```
sudo dpkg -i gyachi_1.1.0-1_i386_gutsy.deb
``` where gyachi_1.1.0-1_i386_gutsy.deb is the name of the .deb you just downloaded.

---

