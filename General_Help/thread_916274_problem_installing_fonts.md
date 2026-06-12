---
title: "problem installing fonts"
date: 2008-09-10
forum: General Help
---

### Post by MountainX on 2008-09-10
I downloaded some ttf fonts and put them into /usr/share/fonts/truetype/

then I did this

```
sudo fc-cache -f
```

to refresh the cache.

But when I open OO, the fonts are not available.

---

### Post by MountainX on 2008-09-10
restarting X solved it.

---

### Post by ad_267 on 2008-09-10
You can also put them in ~/.fonts if they don't need to be for all users.

---

