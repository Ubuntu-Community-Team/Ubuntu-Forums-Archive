---
title: "How to extract img"
date: 2005-11-24
forum: General Help
---

### Post by yyagol on 2005-11-24
Hi is ther a way to extract *.img to the hard drive ?
like burning to a cd , but to a partition insted ?

---

### Post by souled on 2005-11-24
You can mount the image and all of the files will be there. In a terminal type 
```
sudo mount -t iso9660 -o loop (path to image) (mount path)
```
When you mount it, the files contained in the image will be in the folder you mounted it to.

---

