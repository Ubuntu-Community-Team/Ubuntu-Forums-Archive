---
title: "Savage 2 Help"
date: 2008-11-27
forum: General Help
---

### Post by Crimsunwulf on 2008-11-27
I downloaded Savage 2 (for free from the site).  It was installed as a .bin.  Whenever I double click on it to run it (it's saved to the desktop), I get an error message saying there is no program installed to run the file.

Any help on what to do?

---

### Post by taurus on 2008-11-27
Try to see if you can install it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename**.bin
sudo ./**filename**.bin
```
Replace filename with the actual name of the file that you've downloaded.

---

### Post by Crimsunwulf on 2008-11-27
Yep, thank you very much! ^^

---

