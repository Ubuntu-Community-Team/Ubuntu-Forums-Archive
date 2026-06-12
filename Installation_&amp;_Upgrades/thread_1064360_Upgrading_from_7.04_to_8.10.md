---
title: "Upgrading from 7.04 to 8.10"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Ironrat on 2009-02-08
Hi:

I need help. I can't upgrade Ubuntu 7.04 to the nex version because the installer doesn't find the files on the server?

---

### Post by cariboo on 2009-02-08
You have to upgrade from version to version eg:

```
7.04-->7.10-->8.04-->8.10
```

You should be able to follow the update path as gutsy is still available. 

Make sure you disable and ppa archives in System-->Administration-->Software Sources, then press Alt-F2 and type:

```
sudo update-manager -d
```

This should open Update Manager with a list of updates.

Jim

---

### Post by Ironrat on 2009-02-08
I can't upgrade, keeps showing this error:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]

---

