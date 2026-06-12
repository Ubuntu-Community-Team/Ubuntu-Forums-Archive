---
title: "Can't Fully Empty Trash"
date: 2008-09-12
forum: General Help
---

### Post by mikeMarek on 2008-09-12
For some reason, I can not empty out all of my files from the trash can. I have 5 folders that can not be deleted. I get an error message saying "Error: Permission denied". I've tried running Nautilus as root, but still no success. I can not access the trash can from this command:
```
sudo nautilus
```

I'd really appreciate it if anyone could help because those 5 folders take up about 1 GB of space, and is really bugging me :lolflag:

Cheers,
-Mike

---

### Post by StOoZ on 2008-09-12
maybe but just maybe , try deleting these items from the terminal , manually using sudo and rm

---

### Post by chrisccoulson on 2008-09-12
Try:
```
sudo rm -r ~/.local/share/Trash/*
```

---

### Post by dislocated on 2008-09-16
> **chrisccoulson said:**
> Try:
```
sudo rm -r ~/.local/share/Trash/*
```

coincidentally, I had recently run into this problem as well. sudo rm -r did the trick for me.

---

