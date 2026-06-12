---
title: "Need  Help... how do i install winrar..."
date: 2008-08-14
forum: General Help
---

### Post by ahmadfauzi on 2008-08-14
i'm totally new to ubuntu so there a lot for me to learn. how do u install winrar? i try to download but when complete it is unuseable. It is in rar file format. then how do u istall it. please help me...

---

### Post by renzokuken on 2008-08-14
you nee the unrar package from the ubuntu repos.....

either search in synaptic package manager for **unrar**......or alternatively install it using

```
sudo apt-get install unrar
```

then you should be able to extract rar files by simply right clicking them and selecting **Extract to here..**

EDIT: I should probably mention that winrar is for windows (hence the name) and cannot be installed directly in ubuntu (although maybe possible using Wine)....unrar is a linux based equivalent

---

### Post by sayakb on 2008-08-14
```
sudo apt-get install rar unrar-free
```
The default archive manager should be able to handle (create and extract) rar files then.

---

