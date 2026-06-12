---
title: "updating pidgin"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by gt8ost4l on 2009-02-11
does anybody know how i can update pidgin without deletin the old version?

---

### Post by zvacet on 2009-02-12
```
gksudo gedit /etc/apt/sources.list
```

and add this line 

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

