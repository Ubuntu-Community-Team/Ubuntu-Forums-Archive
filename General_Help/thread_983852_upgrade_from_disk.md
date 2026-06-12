---
title: "upgrade from disk?"
date: 2008-11-16
forum: General Help
---

### Post by da.tiger on 2008-11-16
I downloaded the interpid ibex disk.. can i upgrade from hardy to ibex from the disk itself?

---

### Post by prshah on 2008-11-16
> **da.tiger said:**
> I downloaded the interpid ibex disk.. can i upgrade from hardy to ibex from the disk itself?

You can upgrade Hardy to Ibex using only the _alternate_ cd image.

If you've downloaded the live CD image, you cannot use that to upgrade.

If you've downloaded the correct image, it will prompt you to upgrade when you put in the CD (or mount the image); if it doesn't, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo /media/cdrom/cdromupgrade.sh
```

---

