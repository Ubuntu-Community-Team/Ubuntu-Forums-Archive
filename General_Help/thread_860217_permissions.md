---
title: "permissions"
date: 2008-07-15
forum: General Help
---

### Post by mhawas on 2008-07-15
hi ,
i have sound problem with my lenovo 3000 n200 laptop . i found a solution by adding a line in that file " /etc/modprobe.d/alsa-base " but unfortunately i get a message that i don't have permission to save changes on that file :confused:  could someone help me please and tell what to do 

best regards

---

### Post by inteluser on 2008-07-15
In the terminal, instead of typing something like "nano /etc/modprobe.d/alsa-base", type "sudo nano /etc/modprobe.d/alsa-base".  You'll be prompted for your password, and then the text editor will open with sufficient permissions to save the file.

(You may want to create a backup of the file before you do this, as you will also have sufficient permissions to change the file incorrectly and cause bad things.)

---

### Post by sisco311 on 2008-07-15
The file is owned by root.
Press Alt+F2 and open the file as root:
```
gksu gedit /etc/modprobe.d/alsa-base
```

---

### Post by tech0007 on 2008-07-15
use 'gksu' or 'gksudo'

---

### Post by mhawas on 2008-07-16
:lolflag: Thanks to all of you , now sound works properly .

---

