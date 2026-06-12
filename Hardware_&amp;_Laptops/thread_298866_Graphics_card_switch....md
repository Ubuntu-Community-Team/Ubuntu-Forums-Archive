---
title: "Graphics card switch..."
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by DrNick on 2006-11-13
Hi all

I've reciently completed an installation of 6.10 with no problems. However since the installation I've switched over the graphics card in the machine to a PCI TNT2 w/32Mb memory.

X Windows no longer starts as its still using the old driver obviously, so is there a way to run the Xorg setup program again and have it detect the new card, like you could in Fedora, or do I have to edit the xorg.conf file by hand?

If I have to edit the config file by hand, which driver should I use?

Cheers,
Tom

---

### Post by an.echte.trilingue on 2006-11-13
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DrNick on 2006-11-13
> **an.echte.trilingue said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

Cheers :)

---

