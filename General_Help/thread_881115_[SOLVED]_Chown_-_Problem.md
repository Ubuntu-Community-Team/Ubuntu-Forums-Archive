---
title: "[SOLVED] Chown - Problem"
date: 2008-08-05
forum: General Help
---

### Post by primolarry on 2008-08-05
Hi there,

I am having problems trying to "own" a folder.

I have some documents in /media/grande/documentos. 'Grande' is the folder where I mount my /dev/sda3 fat partition. This 'documentos' folder is owned by root, but I'd like to own it with my user, so I can restrict the permissions. But if I try (larry is my user):

```
sudo chown larry /media/grande/documentos/

```

I got an 'Operation not allowed error. And that's it, no more information. The line refering to that partition in /etc/fstab is the following:

```
/dev/sda3	/media/grande	vfat	defaults,umask=0	0	0
```

Could someone point me please?Any help would be really appreciated.

Regards,

---

### Post by pseudo-random on 2008-08-05
have you tried > sudo su
and then chown larry (folder) as root?

---

### Post by sisco311 on 2008-08-05
You can't change the owner of a fat partition with chown.
You can setup the permissionsn in fstab.

change the options to:
> defaults,umask=0007,uid=*username*,gid=*username*

---

### Post by primolarry on 2008-08-06
Thank you sisco311, I'll try as soon as I come back from my job.

Regards,

---

### Post by primolarry on 2008-08-06
Well that did solve the problem, thank you very much.

Regards,

---

