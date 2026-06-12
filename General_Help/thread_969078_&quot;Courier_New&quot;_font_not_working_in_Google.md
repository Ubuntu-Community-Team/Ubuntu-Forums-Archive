---
title: "&quot;Courier New&quot; font not working in Google Documents"
date: 2008-11-03
forum: General Help
---

### Post by tfotherby on 2008-11-03
Does anyone know why when using Google Documents in Firefox 3.0.3 with Ubuntu 8.10, if I select some text and change the font to "Courier New", nothing changes. Is it a problem with Firefox or with Google Documents? Do I need to install a font? If so, how? 

I don't have the same problem in Windows but I did have the same problem in previous versions of Ubuntu (i.e. before 8.10).

---

### Post by copacetickid on 2009-05-05
Had this same exact issue on a fresh install of 9.0.4

```
sudo apt-get install ttf-mscorefints-installer
```This and a restart of FF took care of it for me.

---

### Post by larryn on 2010-08-22
The above sudo apt-get install worked for me if you correct the typo.

---

