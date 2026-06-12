---
title: "Mounting Ubunutu drive in BSD"
date: 2008-10-08
forum: General Help
---

### Post by bigdaddymerk on 2008-10-08
Hi, I'm trying to make a backup of my media storage disk from my main pc (Ubunutu) onto my server FreeBSD 6.2. 

I thought (for somereason) ubuntu wrote in UFS format however when I try and mount using UFS I get; 

```
mount -t ufs /dev/ad4s1 /backup
mount: /dev/ad4s1 on /backup: incorrect super block
```

I've had a quick look around the forums but I can't find a great deal to help, can anyone point me in the right direction please?

Cheers
M

---

### Post by geirha on 2008-10-08
Ubuntu uses ext3 by default, so try with -t ext3.

---

### Post by bigdaddymerk on 2008-10-08
thanks, that appears to have worked. cheers.

---

