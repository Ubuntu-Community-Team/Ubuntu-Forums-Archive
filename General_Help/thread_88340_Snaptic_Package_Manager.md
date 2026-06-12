---
title: "Snaptic Package Manager"
date: 2005-11-10
forum: General Help
---

### Post by Drifter on 2005-11-10
How can I correct these errors in sanptic.

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by RAOF on 2005-11-10
Remove the Breezy-backports lines from your sources.list.  You don't need them, anyway.  You're running breezy ;)

In a terminal, run
```
sudo gedit /etc/apt/sources.list
```
and put a # character in front of the lines with "breezy-backports" in them.

---

### Post by rjwood on 2005-11-10
from a terminal type:
```
sudo gedit /etc/apt/soutces.list
``` and hit enter
A file will appear
remove all the "us." portions of all the lines- only the letters "us" and the dots after the letters.
save the file---close ou of it

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

That should do it for you.

---

### Post by Drifter on 2005-11-10
Thank u rfwood it worked and I appreciate it.

---

