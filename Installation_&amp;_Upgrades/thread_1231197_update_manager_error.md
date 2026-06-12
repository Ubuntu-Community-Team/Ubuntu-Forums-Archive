---
title: "update manager error"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by permant on 2009-08-04
Hi,everybody:
My update manager error!

W: Failed to fetch [http://ubuntu.dormforce.net/ubuntu/pool/main/l/linux/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb](http://ubuntu.dormforce.net/ubuntu/pool/main/l/linux/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb)
  404 Not Found


W: Failed to fetch [http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.28-14.19_all.deb](http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.28-14.19_all.deb)
  404 Not Found

......

So ,how shall I do ?

---

### Post by realzippy on 2009-08-04
..those directories do not exist.Have a look:
[http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/](http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/)

---

### Post by gjoellee on 2009-08-04
> 
..those directories do not exist.Have a look:
[http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/](http://ubuntu.dormforce.net/ubuntu/pool/restricted/l/)

Try running this command:
```
sudo apt-get update && sudo apt-get upgrade
```

Maybe you can change the repo link in /etc/apt/sources.list ?

---

