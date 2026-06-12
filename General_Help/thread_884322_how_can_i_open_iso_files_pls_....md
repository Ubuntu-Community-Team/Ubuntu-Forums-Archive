---
title: "how can i open iso files pls ..."
date: 2008-08-08
forum: General Help
---

### Post by birlindo on 2008-08-08
how can i open iso files pls , is there a compactible program in ubuntu can open iso files ? 



thanks ...

---

### Post by GreenN00b on 2008-08-08
You can open them using archive manager ( right click and select open with archive manager) or you can mount them using mount command.

---

### Post by pparks1 on 2008-08-08
sudo mkdir /mountpoint
sudo mount -o loop -t iso9660 /filename.iso /mountpoint

---

### Post by birlindo on 2008-08-08
thanks for this great help

---

