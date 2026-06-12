---
title: "installing .bin files"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by ghettoman962 on 2009-04-06
ok, i just download savage 2 in a bin format. i'v tried all the "chmod a+x savage.bin" stuff but it never works i always get "no such file or directory". someone help

---

### Post by oldos2er on 2009-04-06
If the file is on your desktop, you first need to run "cd Desktop"

---

### Post by ghettoman962 on 2009-04-07
i did that, typed in the files stuff and it just went back to "Name@ubuntu: ~/Desktop". it's not working

---

### Post by kellemes on 2009-04-07
> **ghettoman962 said:**
> i did that, typed in the files stuff and it just went back to "Name@ubuntu: ~/Desktop". it's not working

```
ls -al
```
Should show you if this this file is executable..
If it's not, you make it executable..
chmod +x <filename>
If it is, execute it..
```
./<filename>
```

---

### Post by ghettoman962 on 2009-04-07
it showed up but after putting in the file name
it says "cannot execute binary file"

---

