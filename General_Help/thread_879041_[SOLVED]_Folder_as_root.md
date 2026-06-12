---
title: "[SOLVED] Folder as root"
date: 2008-08-03
forum: General Help
---

### Post by PCessna on 2008-08-03
Hey all, I know this is kinda dumb to ask, But how do you open a folder as root or unlock it, in my case it's /var/www for apache.

Thanks
-PCessna

---

### Post by dentaku65 on 2008-08-03
You can try:
```
sudo nautilus /var/www
```

---

### Post by tamoneya on 2008-08-03
please use gksudo instead of sudo when running graphical applications.  Sudo will cause permissions issues:
```
gksudo nautilus
```

---

### Post by PCessna on 2008-08-03
> **tamoneya said:**
> please use gksudo instead of sudo when running graphical applications.  Sudo will cause permissions issues:
```
gksudo nautilus
```

```
Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.8 (Ubuntu) Server at localhost Port 80
```
After putting all files :[

Edit: can anyone please help make WWW a non-root folder. I don't want it to be a root folder in the first place

---

### Post by PCessna on 2008-08-03
> **PCessna said:**
> ```
Forbidden

You don't have permission to access /index.html on this server.
Apache/2.2.8 (Ubuntu) Server at localhost Port 80
```
After putting all files :[

Edit: can anyone please help make WWW a non-root folder. I don't want it to be a root folder in the first place
Applyed non-owner permissions to folders and files and no longer is locked. Topic SOLVED

---

