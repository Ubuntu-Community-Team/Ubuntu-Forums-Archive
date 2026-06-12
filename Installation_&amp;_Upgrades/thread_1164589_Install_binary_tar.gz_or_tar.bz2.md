---
title: "Install binary tar.gz or tar.bz2"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-05-19
I was noticing that sometimes when you download a tar.bz2 it contains binaries. I was wondering where I should extract them to or what command I should run to install them.

---

### Post by taurus on 2009-05-19
You can either extract it to your own $HOME (a good place is in ~/bin) if you are the only user or to /opt if you want others to be able to run the program (you need root privilege to do that).  Then, you either need to add the whole path to that binary to your PATH in ~/.bashrc or you have to include the whole path when you want to run it from a terminal.  Of course, you can always create a launcher on the top panel to run it.

---

### Post by pawnrocket on 2009-05-19
In case you don't know PATH is a location of the system The path to your home is /home/your name or ~/your name

---

