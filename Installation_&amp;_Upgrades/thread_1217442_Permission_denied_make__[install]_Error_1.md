---
title: "Permission denied make: *** [install] Error 1"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by ranger_cole on 2009-07-19
I am trying to install xfi drivers, Ubuntu 9.04, but get the following error in the terminal:


jaypugh@jaypugh-desktop:~/Desktop/XFiDrv$ make install
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.28-13-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1


Any ideas??  Your help is very welcome.

---

### Post by SuperSonic4 on 2009-07-19
make install writes to places on the / partition so you need *sudo* to make install

```
sudo make install
```

If you run ```
sudo !!
``` it will run the last command you entered with root priviliges

ie: ```
make install
sudo !!

= sudo make install
```

---

### Post by ranger_cole on 2009-07-20
That worked.  I still do not have sound however.  Thanks for the info.

---

