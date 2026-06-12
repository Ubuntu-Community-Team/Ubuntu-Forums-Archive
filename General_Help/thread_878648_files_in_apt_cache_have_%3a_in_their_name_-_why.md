---
title: "files in apt cache have %3a in their name - why"
date: 2008-08-03
forum: General Help
---

### Post by smokinXP on 2008-08-03
I have some strange file names is my apt cache.
The file names have the characters **%3a** in them.
I have copied the cache to a windows machine to preserve them so I don't have to download them again; I wonder if this is the reason?

_Any_ responses will be gratefully received..,

---

### Post by dexter.deepak on 2008-08-03
those are spaces.

---

### Post by sayakb on 2008-08-03
The files are downloaded exactly the way they are on the hosting server. Just do:
```
sudo dpkg -i *.deb
```
To install the files automatically later when you need to install them. 

**Note:** The apt cache may have 2 different deb files for different versions of the same package. Installing them simultaneously may break your packages. You should rather use AptOnCD to backup and restore your packages.

---

