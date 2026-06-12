---
title: "[SOLVED] .deb"
date: 2008-08-29
forum: General Help
---

### Post by ^^rac on 2008-08-29
How to install a .deb file?

Thanks!!

---

### Post by Elfy on 2008-08-29
You shouldbe able to double click it - gdebi will open and you can then install or using terminal

```
cd /to/wher/it/is
``` and run ```
sudo dpkg -i nameofile.deb
```

or combining the 2 ```
sudo dpkg -i /path/to where/deb is/nameoffile.deb
```

---

### Post by ^^rac on 2008-08-29
> **forestpixie said:**
> You shouldbe able to double click it - gdebi will open and you can then install or using terminal

```
cd /to/wher/it/is
``` and run ```
sudo dpkg -i nameofile.deb
```

or combining the 2 ```
sudo dpkg -i /path/to where/deb is/nameoffile.deb
```

Thanks alot!

---

