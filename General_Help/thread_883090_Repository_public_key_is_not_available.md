---
title: "Repository public key is not available"
date: 2008-08-07
forum: General Help
---

### Post by Coldmiser487 on 2008-08-07
[porn](http://emo-porn.com)
[amateur porn](http://camrevenge.com)
[dubstep](http://n3k4.com)

---

### Post by Coldmiser487 on 2008-08-11
bump

---

### Post by Seisen on 2008-08-12
Try ```
wget -q ftp://ftp.berlios.de/pub/griffith/Release.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Coldmiser487 on 2008-08-12
The response to that produces:

```
gpg: no valid OpenPGP data found.
```

---

### Post by Coldmiser487 on 2008-08-17
bump

---

### Post by colo505 on 2010-09-03
wget -q [ftp://ftp.berlios.de/pub/griffith/Release.gpg](ftp://ftp.berlios.de/pub/griffith/Release.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by jcolyn on 2010-09-03
> **Coldmiser487 said:**
> The response to that produces:

```
gpg: no valid OpenPGP data found.
```

You will probably find the key in your home folder. Go to your SYNAPTIC package manager settings-repositories-authentication and use the import function.

---

