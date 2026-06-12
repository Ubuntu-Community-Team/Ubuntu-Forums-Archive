---
title: "gparted help"
date: 2008-08-16
forum: General Help
---

### Post by Dan7356 on 2008-08-16
hey, im trying to resize a partion with gparted but it isnt working, when i resize the ntfs partion i want to resize i get an error saying it is already corrct size or somthing like that, i need to resize this partion so i can install xp on my computer again. but this partion also has over 100gb of daa that i have no way to backup so i cant reformat it, can anyone please help me!!!!!??????

Partions:
60gb ext3 [Ubuntu]
1.4gb Swap
232gb ntfs [Data Drive]

---

### Post by anathema415 on 2008-08-16
???

---

### Post by tfosorcim on 2008-08-16
Is the NTFS partition inside a extended partition? If so you need to resize the NTFS partition then the extended partition. You can't resize the extended partition if the partitions inside it are using all the space.

---

