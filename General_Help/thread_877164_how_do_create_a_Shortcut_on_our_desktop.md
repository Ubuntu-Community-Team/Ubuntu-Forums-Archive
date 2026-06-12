---
title: "how do create a Shortcut on our desktop"
date: 2008-08-01
forum: General Help
---

### Post by robotman5 on 2008-08-01
i just wanna make a Shortcut for my HardDrive  can someone Help?:(

---

### Post by LowSky on 2008-08-01
unless you have edited nautilus, mounted hard drives should show up on the desktop already

---

### Post by robotman5 on 2008-08-01
> **LowSky said:**
> unless you have edited nautilus, mounted hard drives should show up on the desktop already



How do i do that? Lowsky?

---

### Post by dexter.deepak on 2008-08-01
type in a terminal :
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'true'
```

---

### Post by robotman5 on 2008-08-01
it didnt do anything dex and bool doesnt exist

---

