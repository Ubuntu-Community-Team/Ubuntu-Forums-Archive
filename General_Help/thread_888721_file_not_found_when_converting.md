---
title: "file not found when converting"
date: 2008-08-13
forum: General Help
---

### Post by ranger_cole on 2008-08-13
I am trying to convert a .rpm print driver to a.deb using the terminal.
Here is the error message
jaypugh@jaypugh-desktop:~$ sudo alien Fuji.rpm
File "Fuji.rpm" not found.
jaypugh@jaypugh-desktop:~$ 

It is right there on the desktop.  I am still learning Ubuntu 8.04  and this is probably a simple fix.

---

### Post by Nepherte on 2008-08-13
You have to navigate to the directory where the file resides first. You're now in your home director (the '~' or also /home/yourusername). So cd to Desktop:
```
cd Desktop
```

---

### Post by ranger_cole on 2008-08-13
That fixed it.

---

