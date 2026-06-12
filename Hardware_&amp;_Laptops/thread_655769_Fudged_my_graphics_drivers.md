---
title: "Fudged my graphics drivers"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by JuneauPM on 2008-01-01
I'm looking for a way to revert my system config to a previous state or reset my graphics driver to default through the "recovery console". I'm a new user and I got in over my head trying to install drivers for my 945gm, and now when I boot up all I get on my screen is a series of tan and black horizontal lines. I can still access the recovery mode but I have no idea where to start.

---

### Post by taurus on 2008-01-01
```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by JuneauPM on 2008-01-01
Thanks, worked great.

---

