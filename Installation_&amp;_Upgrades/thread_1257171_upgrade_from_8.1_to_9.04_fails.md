---
title: "upgrade from 8.1 to 9.04 fails"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by gkiteguy on 2009-09-03
I attempted to use the upgrade feature to upgrade to the 9.04 release which failed to fetch.  It fails with these messages:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release amd64 (20090121)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


It then just closes. 

Apparenntly the normal update lists have been failing also.  

Can someone please help. 

Gkiteguy

---

### Post by zvacet on 2009-09-04
Edit your sources list with 

```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of line referring to hardy cdrom.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn´t work type 

```
cat /etc/apt/sources.list
```

and post output here.

---

### Post by gkiteguy on 2009-09-05
Thanks. I will make note of that trick.  Now I have to tweak 9.04.  Once again thanks.

---

