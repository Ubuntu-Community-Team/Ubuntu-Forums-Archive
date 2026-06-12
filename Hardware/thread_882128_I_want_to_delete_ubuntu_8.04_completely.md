---
title: "I want to delete ubuntu 8.04 completely"
date: 2008-08-06
forum: Hardware
---

### Post by Millie da kidd on 2008-08-06
I am not dual booting it with nothing.
Ubuntu 8.04 is the only operating system i have on my acer.
i want to delete it completely so i can use my acer system restore disk.

---

### Post by kspncr on 2008-08-06
You should be able to just use the restore disk without deleting it: typically those disks reformat the hard drive so you don't even have to worry about it.

---

### Post by Millie da kidd on 2008-08-06
> **kspncr said:**
> You should be able to just use the restore disk without deleting it: typically those disks reformat the hard drive so you don't even have to worry about it.

People have told me that Acer recovery disk may be expecting something on my hard disk that it can't find. It may be something that the Ubuntu installed/wrote to the boot sector.

---

### Post by hgfdsa on 2008-08-06
> **Millie da kidd said:**
> People have told me that Acer recovery disk may be expecting something on my hard disk that it can't find. It may be something that the Ubuntu installed/wrote to the boot sector.
Is acer the one that places recovery data on hard drives in hidden partitions that are difficult to access and sometimes accidentally deleted?

---

### Post by Millie da kidd on 2008-08-06
> **hgfdsa said:**
> Is acer the one that places recovery data on hard drives in hidden partitions that are difficult to access and sometimes accidentally deleted?

Hm I dont know.What do you recommend me to do?

---

### Post by doas777 on 2008-08-06
you can always boot to the live CD and use parted or fdisk or whatever to remove the existing partition. this probably won;t help your issue however. 
if you want a gui, i recomend gparted (which is conveniently isntalled on the livecd).

there is likely a means to get the restore disk to work, so I would focus on that. 

good luck,

---

### Post by steveneddy on 2008-08-06
Just stick the recovery cd in and see what happens.

---

