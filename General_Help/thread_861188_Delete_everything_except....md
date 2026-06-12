---
title: "Delete everything except..."
date: 2008-07-16
forum: General Help
---

### Post by edbyford on 2008-07-16
There are a load of .ini and .txt files left over in my pictures folder which I copied from my windows computer.

How do I delete every file in this folder (and subfolders) except for the .jpg and .jpeg files?

---

### Post by rraj.be on 2008-07-16
You can delete all .txt entries in a folder by 
```

rm *.txt

rm *.ini
```

---

### Post by willie_wang on 2008-07-16
or... you could move all your jpg and jpeg files temporarily into another folder. then delete all the other files in the current folder then mv the files back.

```
mkdir tmp
mv *.jpg tmp
mv *.jpeg tmp
rm *
mv tmp/* .
rm -r tmp
```

---

