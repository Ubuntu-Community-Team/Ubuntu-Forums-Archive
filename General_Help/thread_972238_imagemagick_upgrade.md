---
title: "imagemagick upgrade"
date: 2008-11-05
forum: General Help
---

### Post by nbo10 on 2008-11-05
Hi I'm using 7.10 with imagemagick version 6.2.4 how can I upgrade to version 6.4.5? Thanks

---

### Post by Partyboi2 on 2008-11-06
Google and see if you can find a deb package for imagemagick 6.2.4. If you can not find one then you can compile it from source. If you don't mind using 6.4.4
You can download the source from [[COLOR=Blue]here[/COLOR]]("http://www.imagemagick.org/www/install-source.html#unix") and follow the instruction on installing it.
You will need to install the build-essential and installing imagemagick dev packages will be useful also as well.
```
sudo apt-get install build-essential
sudo apt-get build-dep imagemagick

```

---

