---
title: "plesk 7.5.4 over top of ubuntu 5.1 breezy badger??"
date: 2005-12-02
forum: General Help
---

### Post by ryedawg on 2005-12-02
after a few setup hurdles ive finally got a solid working setup of the breezy badger and I love it. now the problem is iwant to install plesk 7.5 reloaded (the latest version) on here.....the plesk 7.5 supports ubuntu 5.04 so i would assume it supports the newest version of ubuntu as well(breezy badger 5.1)....but when im installing it it kicks an error out and i am begginning to wonder if its possible to do this.......has anyone tried installing this yet onto breezy badger or should i drop down to the hoary 5.04???

the error it kicks out is

Building dependecy tree.......
E: Version '7.5.4-ubuntu5.04.build75050824.12'  for 'psa' was not found

---

### Post by dutchie on 2005-12-05
I'd be interested to know if you got this working, as I may do the same.

Cheers,
Dutchie

---

### Post by hallikpapa on 2005-12-25
I am trying to get this working too. I have a broken package it won't let me install, uninstall, or repair. What do you do in this situation?

---

### Post by Bailx on 2006-01-02
plesk support:

Unfortunately we don't support the 5.10 version of Ubuntu. This version will
be supported in the February/March time frame... Plesk currently will not
work on this software.

---

### Post by SyphOn on 2006-01-17
Yes i got it working.

Download the Ubuntu 5.04 Autoinstaller build 75050908.11 from the swsoft website:

[http://www.swsoft.com/en/download/plesk75reloaded/](http://www.swsoft.com/en/download/plesk75reloaded/)

put in in let's say ~/plesk

```
chmod +x Autoinstaller
```

If MySQL is installed make a user called 'admin' with password 'setup' or leave the root password empty (not recommended). If MySQL is not installed, don't install it ;)

```
./autoinstaller
```

Follow onscreen instructions. Dont forget to choose the swsoft server as installation media.

If the installer fails after building dependencies, processing package list or returns to te first install screen, try to do: 

```
ctrl-c
apt-get update
apt-get -f install
```

Then run the installer again.

---

### Post by SteveHillier on 2008-04-06
> **ryedawg said:**
> after a few setup hurdles ive finally got a solid working setup of the breezy badger and I love it. now the problem is iwant to install plesk 7.5 reloaded (the latest version) on here.....the plesk 7.5 supports ubuntu 5.04 so i would assume it supports the newest version of ubuntu as well(breezy badger 5.1)....but when im installing it it kicks an error out and i am begginning to wonder if its possible to do this.......has anyone tried installing this yet onto breezy badger or should i drop down to the hoary 5.04???

the error it kicks out is

Building dependecy tree.......
E: Version '7.5.4-ubuntu5.04.build75050824.12'  for 'psa' was not found

I still got this maeeage 30 months later on.

---

### Post by SteveHillier on 2008-04-06
> **hallikpapa said:**
> I am trying to get this working too. I have a broken package it won't let me install, uninstall, or repair. What do you do in this situation?

I have had this and needed to do ```
apt-get -f install
```to rebuild the dependency tree.

---

