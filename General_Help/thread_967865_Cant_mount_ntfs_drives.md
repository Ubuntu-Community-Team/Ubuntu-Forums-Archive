---
title: "Cant mount ntfs drives"
date: 2008-11-02
forum: General Help
---

### Post by charanpreethu on 2008-11-02
I cant mount ntfs drives wen i restart my computer from windows to ubuntu...I get error msg saying cant mount volume...

---

### Post by taurus on 2008-11-02
How do you mount your window partition?  Do you try to mount it by hand or do you have an entry in /etc/fstab to mount it automatically each time you boot Ubuntu?

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by charanpreethu on 2008-11-02
every time wen i boot ubuntu...i go to places n mount from ther...

---

