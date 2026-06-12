---
title: "Uninstalling some email packages"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by srijith on 2005-07-31
I would like to trim up installed package list a bit and was hoping to uninstall some email packages. But they seem to have dependencies that I am afraid would create a mess if removed. Can anyone let me know whether they are ok to remove? The packages are:

1. fetchmail: dependency - "ubuntu desktop"
2. mailx: dependency - "mysql server"
3. postfix: dependencies - "mysql server", "ubuntu desktop", "mailx", "mutt", "anacron" , "lsb", "at"..
4. procmail: dependency "ubuntu dekstop"

I would like to keep the mysql server, but I can't see any reason why it needs mailx or procmail.

---

### Post by scorcher on 2005-07-31
[QUOTE=srijith]
1. fetchmail: dependency - "ubuntu desktop"
4. procmail: dependency "ubuntu dekstop"
[/QUOTE]

Removing the ubuntu-desktop package won't hurt anything.

ubuntu-desktop is a meta-package that depends on the default desktop packages. 

If you remove ubuntu-desktop and later upgrade to the next release of Ubuntu it is a good idea to reinstall it to make sure you have any new desktop packages.

---

