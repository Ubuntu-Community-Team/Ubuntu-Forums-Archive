---
title: "Can't update wine"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by 2LSS on 2009-06-23
I ran update manager today and all went good until I got this message:

W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.23~winehq0~ubuntu~8.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_1.1.23~winehq0~ubuntu~8.04-0ubuntu1_i386.deb)
  404 Not Found

I checked the index at wine.budgetdedicated.com/apt/pool/main/w/wine/ and the closest thing I found was: wine_1.1.24~winehq0~ubuntu~8.04-0ubuntu1_i386.deb

Update manager is looking for the wrong file.

Can somebody please explain how to fix this?

---

### Post by mk1w86 on 2009-06-24
Try running

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by 2LSS on 2009-07-01
This seemed to do the trick, Thanks!

---

