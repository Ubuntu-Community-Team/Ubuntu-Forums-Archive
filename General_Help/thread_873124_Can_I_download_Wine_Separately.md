---
title: "Can I download Wine Separately?"
date: 2008-07-28
forum: General Help
---

### Post by jras20 on 2008-07-28
I was wondering if I could download Wine Separately instead of in the packaging or terminal?  I'd like to have 1.0 just in case I decide to use 8.04 Ubuntu on a older computer that is not connected to the Internet.
Thanks

---

### Post by bodhi.zazen on 2008-07-28
Yes ...

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by jras20 on 2008-07-28
> **bodhi.zazen said:**
> Yes ...

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

Thanks

---

### Post by geirha on 2008-07-28
You can use aptitude to download without installing. ```
aptitude download wine
``` (without sudo in front) will download the wine package to the current directory. You can then copy that .deb package to your networkless computer and double-click it to install, or from a terminal: ```
sudo dpkg -i wine*.deb
```

---

