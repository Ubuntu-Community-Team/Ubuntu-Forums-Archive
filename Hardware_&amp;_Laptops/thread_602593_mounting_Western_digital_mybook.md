---
title: "mounting Western digital mybook"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by chrisplod on 2007-11-04
Hey Peeps,

Ive got a WD mybook 500gb, which was all working, but now says "you do not have permission to mount this drive"

any ideas how I can remount it permenantly, and so that it can be written to also?

cheers
chris

---

### Post by lucas448 on 2008-02-19
bump.
mine to. any clue?

---

### Post by Yellow Pasque on 2008-02-19
Mount it with sudo?
Connect your drive and give us output from these commands:
```
sudo fdisk -l
sudo lshw -C disk
```

---

