---
title: "[SOLVED] removable Hard drive has no privledges"
date: 2008-11-11
forum: Hardware
---

### Post by bails on 2008-11-11
i have a western digital 120 gig removable hd which is formatted for linux. i have access to all of the files on the drive but i cannot put any new files onto the drive. it says that i don't have the privlidges to be able to do that. i look at the properties, privledges tab. it says there are no privledges. how do i add privledges to this removable hard drive?

---

### Post by bails on 2008-11-12
ok so i figured out my own answer. you type in terminal:

> sudo chown -R <username> <where the disk is mounted>

the chown = change ownership
the -R = do this for all the subfolders and files

THANKS N E WAY FOR THE HELP!!!

---

### Post by pelle.k on 2008-11-12
I would have helped you out, but obviously i wasn't quick enough :)

---

