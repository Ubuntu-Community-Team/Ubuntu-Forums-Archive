---
title: "apt-get update don't work / 9.04"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by bartabbas on 2009-04-29
Hello,

I'm trying to build a custom iso from ubuntu 9.04 

*here's the answer when I type :*

root@BD26F99:/# apt-get update
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release.gpg
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Translation-fr
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Translation-fr
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Packages
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Packages
Lecture des listes de paquets... Erreur !
E: Impossible de réaliser un mapping de 25165824 octets en mémoire - mmap (19 Aucun périphérique de ce type)
W: Unable to munmap
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.

*If I try to change APT config :* [IMG]http://forum.ubuntu-fr.org/img/smilies/smile.png[/IMG]

root@BD26F99:/# echo 'APT::Cache-Limit "20000000000"; ' > /etc/apt/apt.conf.d/30cache
root@BD26F99:/# apt-get update
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release.gpg
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Translation-fr
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Translation-fr
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Packages
Atteint [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Packages
Lecture des listes de paquets... Erreur !
E: Impossible de réaliser un mapping de 2147483647 octets en mémoire - mmap (19 Aucun périphérique de ce type)
W: Unable to munmap
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.
root@BD26F99:/#                  

Thanks for your help,

---

