---
title: "[SOLVED] Make nautilus show mounted volumes"
date: 2008-09-03
forum: General Help
---

### Post by u-slayer on 2008-09-03
Hi. I have a large number of volumes that I mount with truecrypt and I normally put them in the /mnt directory. However, nautilus doesn't show this, it only shows volumes in the /media dir. Also it should show the volume size for all the volumes, not just the plaintext ones. How can I fix this?

---

### Post by u-slayer on 2008-09-04
bump

---

### Post by u-slayer on 2008-09-09
I solved this myself. I just deleted /mnt and made a symbolic link from /mnt /media. Now everything I mount in /mnt appears in /media. and will show up in nautilus:lolflag:

```

#make sure nothing is mounted in /mnt before you try this!
rm -r /mnt
ln -s /media /mnt

```

---

