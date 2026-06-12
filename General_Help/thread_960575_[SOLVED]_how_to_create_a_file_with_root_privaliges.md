---
title: "[SOLVED] how to create a file with root privaliges"
date: 2008-10-27
forum: General Help
---

### Post by sneeks on 2008-10-27
i need to create a file to copy some fonts into,which is a usr /directory.
but when i try to there is no option to create a new folder.
is there a line command i can use to do it ?

---

### Post by bodhi.zazen on 2008-10-27
sudo cp file /usr

Or use

```
gksu nautilus
``` if you wish to cut and paste.

---

### Post by oldos2er on 2008-10-27
> **sneeks said:**
> i need to create a file to copy some fonts into,which is a usr /directory.
but when i try to there is no option to create a new folder.
is there a line command i can use to do it ?

 sudo mkdir [directory name]

---

### Post by Arabiest on 2008-10-27
Thanks gents 4 the hint

---

### Post by oldos2er on 2008-10-27
> **Arabiest said:**
> Thanks gents 4 the hint

 I'm not a "gent," but you're welcome.

---

