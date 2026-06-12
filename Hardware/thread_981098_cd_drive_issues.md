---
title: "cd drive issues"
date: 2008-11-13
forum: Hardware
---

### Post by rstimpymike on 2008-11-13
i recently setup my computer for a dual boot of ubuntu and windows vista... i had partitioned my harddrive to have another chunk of storage on vista...after doing that i realized that my cd drive isnt being recognized..can anyone help?

---

### Post by sisco311 on 2008-11-13
open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
cat /etc/fstab
```
and
```
sudo lshw -C disk
```

---

### Post by lukjad on 2008-11-13
Do you mean that the CD drive doesn't work in Vista or just doesn't work? Or do you mean that Ubuntu doesn't load when you insert the disk into the drive and restart?

---

### Post by rstimpymike on 2008-11-13
it doesnt work in vista idk about ubuntu

---

