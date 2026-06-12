---
title: "[SOLVED] trash"
date: 2008-07-16
forum: General Help
---

### Post by pikabuntu on 2008-07-16
I copied a file from a cd onto my desktop by accident and then threw it in the trash, but it says i don't have permission to delete it permanently.  How do i give myself this permission?

---

### Post by dracayr on 2008-07-16
press alt+F2 and type gksudo nautilus, then press enter

dracayr

---

### Post by Ryadt on 2008-07-16
```
gksudo nautilus
```
Then you can delete the file from there.

---

### Post by dracayr on 2008-07-16
Oh, your trash is in $HOME/.local/share/Trash/files (in hardy). to be able to see the .local directory, press Ctrl+H in nautilus

dracayr

---

### Post by lukjad on 2008-07-16
Go to a terminal and type:
```
sudo rm -r ~/.local/share/Trash/files/
```

---

