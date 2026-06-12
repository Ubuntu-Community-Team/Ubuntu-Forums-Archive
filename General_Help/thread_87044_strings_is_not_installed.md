---
title: "strings is not installed"
date: 2005-11-07
forum: General Help
---

### Post by eeGhoong0ais on 2005-11-07
... maybe it never was; it's not a program I want to use very often, but today I did, and was surprised to find it not there.

Anyone know what package it's in? The word "strings" is so common that searching in Synaptic is next to useless.

In case anyone is wondering why I wanted it, I was I trying to find metadata in a JPEG that *eog* claimed didn't exist. I have now found it with *identify* so the emergency is over, but I'd still like to have *strings* around when I want it.

Thanks ...

---

### Post by ranf on 2005-11-07
[QUOTE=Etiol]... maybe it never was; it's not a program I want to use very often, but today I did, and was surprised to find it not there.

Anyone know what package it's in? The word "strings" is so common that searching in Synaptic is next to useless.
[/QUOTE]
Visit [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
and use the `Search the contents of packages' search.

---

### Post by ubuntumaneh on 2005-11-07
Try also (in terminal):

apt-cache search strings|grep strings

I was not able to find, but im in Hoary right now.

---

### Post by eeGhoong0ais on 2005-11-07
Brilliant, thanks - the package I needed was *binutils.*

---

