---
title: "Tried to extract iso... I messed up, bad."
date: 2008-09-04
forum: General Help
---

### Post by wisedrunkard on 2008-09-04
So I tried to extract the cod4 iso onto my desktop with this command:

sudo mount -o loop /home/ryan/Desktop/COD4.iso /home/ryan/Desktop/

Now all the folders I had before are gone and replace with read only files I can't seem to delete.

Is there anyway to delete these files and get back the original ones?!

Much Thanks

---

### Post by justleen on 2008-09-04
```
sudo umount /home/ryan/Desktop
```

CDROM are read only, so a mounted ISO image is read only to, hence you cannot delete any files : you've mounted a CDROM on your home dir.

Tip:the /mnt dir is a good dir to mount CD's on..

---

### Post by Archmage on 2008-09-04
Did you umonut the ISO?

---

### Post by compiledkernel on 2008-09-04
Closing.

---

