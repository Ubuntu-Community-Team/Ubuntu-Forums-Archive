---
title: "problem removing smplayer"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by sonusikka on 2009-08-13
hi..
please help me out in uninstalling smplayer .....when i execute sudo apt-get remove smplayer it gives following error!!

dpkg: unrecoverable fatal error, aborting:
 unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Partyboi2 on 2009-08-13
Hi, try making some room by cleaning out the cache, open a terminal (Applications>Accessories>Terminal) then
```
sudo apt-get clean
sudo apt-get remove smplayer
```

---

### Post by sonusikka on 2009-08-13
thanxs, it worked....:)

---

### Post by Partyboi2 on 2009-08-13
Happy to help, if you keep running into problems with not having enough space left, you might want to consider increasing the size of your Ubuntu partition if you are able to.

---

