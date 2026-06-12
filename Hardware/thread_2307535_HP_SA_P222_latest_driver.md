---
title: "HP SA P222 latest driver"
date: 2015-12-26
forum: Hardware
---

### Post by buntuepic on 2015-12-26
Hello,

Does anyone know the link to download the latest version of "hpsa" driver for 12.04.2 ?

Thanks

---

### Post by Bucky Ball on 2015-12-26
12.04.2 is no longer supported. You need to get to the .5 and that might help or even fix your problems. Run these three commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

And for future reference, [see this]("https://wiki.ubuntu.com/Releases").

---

