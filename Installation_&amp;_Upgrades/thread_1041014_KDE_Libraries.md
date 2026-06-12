---
title: "KDE Libraries"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by gokbektas on 2009-01-16
I'm trying to compile krusader but there is something wrong:


```
kde-config --prefix
/usr
```

```

./configure --prefix=/usr
.
.
.
lots of lines.
.
.
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
```


Ubuntu 8.10

KDE is under usr/include/KDE as default.

Any opinions? There is KDE but it can not complete the operation.

---

### Post by Partyboi2 on 2009-01-16
krusader is available from the ubuntu repos, you can search synaptic package manager for it or you can install from the terminal
```
sudo apt-get install krusader
```
Unless of course there is a reason you need to compile it ;)

---

