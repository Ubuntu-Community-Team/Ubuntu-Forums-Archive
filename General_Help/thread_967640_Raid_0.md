---
title: "Raid 0"
date: 2008-11-02
forum: General Help
---

### Post by Stalker72 on 2008-11-02
I've been using Ubuntu on my hard drive for a while now. In Windows, I ran a RAID 0 configuration (I thought) until I found out that one hard drive wasn't working. I sent it back to where I bought it and just got it back again.

Can I run Ubuntu in RAID 0? Is there something I have to do during installation?

Thanks,

Stalker72

---

### Post by Stalker72 on 2008-11-02
Bump!

Stalker72

---

### Post by Stalker72 on 2008-11-02
Bump!

Stalker72

---

### Post by fjgaude on 2008-11-02
We be confused... raid0 requires that both drives work correctly, else no data.

Sure you can software raid two drives in Ubunut through a program called **mdadm**. You cannot boot from a raid0 array, nor from a raid5. Some have using raid1.

---

### Post by lukjad on 2008-11-02
Also, why do you wish to use RAID 0? It doesn't help prevent data loss.

---

### Post by psusi on 2008-11-05
You use raid0 because you want speed.  You can boot from raid0 or raid5 if you have a hardware or fake hardware raid controller.  Many common motherboards these days come with a built in fake hardware raid controller, which you can get working under Ubuntu.  It takes a little work to get Intrepid to install properly from the livecd, but I have heard that it works fine from the alternate cd.

---

### Post by lukjad on 2008-11-05
Ah, I see. I asked my teachers, but they just said it was a stupid idea. Nice to know. Thanks!

---

