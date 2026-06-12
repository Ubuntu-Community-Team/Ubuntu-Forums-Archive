---
title: "RPM on Ubuntu"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Plasma_Snake on 2009-05-11
Can I install .rpm files in Ubuntu? If yes then How?

---

### Post by _Purple_ on 2009-05-11
Why don't you search for the .deb file of that particular package?

---

### Post by sgosnell on 2009-05-11
Yes, by installing alien.  The conversion isn't always perfect, though.  It's much better if you can find a .deb package, but if you can't, alien should be able to do the installation.

---

### Post by geraldvillorente on 2009-05-11
yes. Use the alien command
use apt-get to install
```

sudo apt-get install alien

```
then
```

man alien

```

---

