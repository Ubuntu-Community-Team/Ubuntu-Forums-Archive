---
title: "Palm hotsync problem and solution"
date: 2004-11-15
forum: Hardware &amp; Laptops
---

### Post by costoa on 2004-11-15
There seems to be a problem with gpilotd and hotsyncing a Tungsten E. gpilotd would crash when trying to backup "ImgFile-Foto". 

The solution is to edit $HOME/.gnome2/gnome-pilot.d/backup-conduit and change

```
exclude_file=
```
to
```
exclude_file=ImgFile-Foto Jpeg-Foto
```

This is a problem with gpilotd and not Ubuntu.

---

