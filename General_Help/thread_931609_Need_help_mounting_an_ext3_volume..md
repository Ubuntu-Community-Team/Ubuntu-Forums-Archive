---
title: "Need help mounting an ext3 volume."
date: 2008-09-27
forum: General Help
---

### Post by hal1984 on 2008-09-27
I have created a ext3 logical partition with gparted. The system recognized it quickly, but when I mount the partition in Gnome menu it's only with read permission. It didn't happen with others partitions I have created (fat32 and ntfs). 
How could I give it write permission?

Sorry my english.

---

### Post by wolfen69 on 2008-09-27
try ```
sudo chmod -R ug+w /media/name_of_drive
```

---

### Post by hal1984 on 2008-09-28
> **wolfen69 said:**
> try ```
sudo chmod -R ug+w /media/name_of_drive
```

Thank you very much.

---

