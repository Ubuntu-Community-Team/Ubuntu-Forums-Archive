---
title: "Weird Package Directories"
date: 2008-09-24
forum: General Help
---

### Post by Xonara on 2008-09-24
Whenever I install a package, it places all it's files in weird directories like /lib/whee/ and /etc/whee/ and so on. At first this seems to make sense, but it makes it hard to browse the package's entire contents. It'd be nice if there was a way to configure ubuntu to install programs like:

~/Programs/whee/docs
~/Programs/whee/etc

It'd make it easier to do things like, say, install mods for a game when an installer for the mod isn't provided. When I'm looking for a specific directory it's painful to have to look up the package's name every time I go to /lib/ or /etc/ or whatever. Is there a specific reason that packages are structured like this?

---

### Post by Titan8990 on 2008-09-24
The Linux filesystem has always been this way. /etc/ is where your config files are located and typically /usr/ is where your programs will go. A good way to find where a program in located is the whereis command:

jordan@einstein:~$ whereis dia
dia: /usr/bin/dia /usr/lib/dia /usr/share/dia /usr/share/man/man1/dia.1.gz

---

### Post by Xonara on 2008-09-25
Thanks. I figured it would be pretty much impossible to reconfigure it to do thAt but it looks like that whereis command could be useful. :)

---

