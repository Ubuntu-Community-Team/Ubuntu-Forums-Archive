---
title: "iPod user write privalages"
date: 2010-05-15
forum: Hardware
---

### Post by styleruk on 2010-05-15
Hi

I have what seems a simple problem, I can mount my 80GB ipod no problem and have mounted it in the fstab as /media/ipod.  I can see all the files, however, I can't seem to write to it unless I am as sudo user, ie sudo nautilus, then I can write to it.  
From sudo nautilus, I can't change the owner.  I have tried...

sudo chown -R simon:simon /media/ipod
and..
sudo chmod -R 755 /media/ipod

Still no change.  Not a major problem really as every time I write files to it I sudo nautilus, but it is a pain.

Can anyone help?

PS:  I have Ubuntu 10.04

Regards
Si

---

### Post by mr clark25 on 2010-05-19
maybe add a launcher to your panel to start nautilus as root and just put up with it?

---

