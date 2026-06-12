---
title: "Does WebDAV work apache2/8.04?"
date: 2008-10-07
forum: General Help
---

### Post by Sesshomurai on 2008-10-07
Hi,
  I've been trying many tutorials[1] to set up WebDAV on Ubuntu 8.04 with apache2. It seems easy enough, but I cannot access the share from a browser or mount it or connect to it. Even from another machine, It says "Forbidden". Even after I provide the correct login.

What's the trick to access a apache2 WebDAV folder locally or remotely?

thank you!!!
Sessh

[1] [http://www.debianadmin.com/webdav-configuration-with-apache2-on-debian-etch.html](http://www.debianadmin.com/webdav-configuration-with-apache2-on-debian-etch.html)

---

### Post by KrakHT on 2008-12-03
I have. Not 100% (the securing part), but I have gotten it to work.

I followed this, as a guide:
[http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622](http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622)

I had to edit /etc/apache2/mods_available/dav_fs.conf to point to my DavLockDB path.

I can browse it, and map it on a windows box, read, write, all working. But I cant get the security part to work. Go figure.

---

