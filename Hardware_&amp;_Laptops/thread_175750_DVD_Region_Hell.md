---
title: "DVD Region Hell"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by reuben on 2006-05-13
I am authoring my own dvd (based on a video I made) using tovid (which uses dvdauthor). When I try to view my dvd on my sony dvd player, it tells me that there's a region problem... 

I tried using ifoedit (under wine) to clear the region; that still didn't work. Where's the problem? My burner or my player? And what's the solution?

---

### Post by reuben on 2006-05-14
bump. Interested in this :)

---

### Post by xyz on 2006-05-14
This is weird.
Is your DMA on?
```
 sudo hdparm -d 1 /dev/hdc

```

---

### Post by reuben on 2006-05-14
Yep, that says it's on.

---

### Post by handy on 2006-05-15
If it is your DVD drive, perhaps you can solve the problem by flashing the ROM, with a ***region free*** firmware update?

The [**Firmware Page**]("http://forum.rpc1.org/portal.php") may be of help!

---

