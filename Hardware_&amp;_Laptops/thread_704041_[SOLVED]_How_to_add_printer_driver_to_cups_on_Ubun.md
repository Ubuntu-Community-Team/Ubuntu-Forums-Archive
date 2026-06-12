---
title: "[SOLVED] How to add printer driver to cups on Ubuntu Server"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by julien-1993 on 2008-02-21
I have just finish installing a minimal Ubuntu 7.10 gnome environnement using the server CD.

I would like to have easy printer support in gnome like there is in the Ubuntu Desktop version.

What I have done is: 

```
sudo apt-get install cupsys gnome-cups-manager cups-pdf
```

but when I go in System->Administration->Printing and add a new printer I dont have the manufacturer list I used to have when I was using Ubuntu Desktop.

I would like to have it to install cleanly and easyly my Parrallel Canon BJC-4400

Thank you
Julien

---

### Post by julien-1993 on 2008-02-22
solved it by myself, needed:
```

sudo apt-get install cupsys-driver-gutenprint
```

---

