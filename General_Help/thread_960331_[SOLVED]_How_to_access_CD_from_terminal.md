---
title: "[SOLVED] How to access CD from terminal"
date: 2008-10-27
forum: General Help
---

### Post by morty35 on 2008-10-27
This is a really simple question.  I am new to Linux and I need to run software from the CD as root.  So that means I need to use the terminal.  However, I don't know how to get to the CD drive from the terminal.  I tried just using cd .. but I can't get to the entire computer access.

---

### Post by geirha on 2008-10-27
CDs get mounted in /media as /media/cdrom0 /media/cdrom1 etc, depending on how many cd drives you have, so try:
```

cd /media
ls
cd cdrom0
ls

```

---

### Post by Jense on 2008-10-27
So I don't really know what you mean by "entire computer access". If the disc is allready mounted you can get there by> cd /media/cdrom0/
You can then look at the contents by > ls
For root acces do a > sudo su

---

