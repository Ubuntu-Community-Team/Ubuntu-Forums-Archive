---
title: "Upgrade to Flash 10 on Netbook"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by lewisforlife on 2009-09-07
I have a Dell Mini Netbook with Ubuntu 8.04, intel atom.  I want to upgrade to Flash 10, but when I try to install the .deb that can be downloaded from adobe.com, I get that my computer is an invalid architecture for the .deb file.  How can I upgrade to the latest version of flash?

Thanks

---

### Post by zvacet on 2009-09-08
Edit your source list in terminal with command

```
gksudo gedit /etc/apt/sources.list
```

add line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

Save and close file.In terminal 

```
sudo apt-get update
```

System>admin>synaptic>in search box type adobe-flashplugin and when you find it install it.

---

