---
title: "Cloning to a new drive"
date: 2008-08-26
forum: General Help
---

### Post by Turrat on 2008-08-26
I posted something similar to this in another category but I think this fits better here. A couple years ago I installed Windows XP on my machine because I got a free disc and one-use key from the university I attended. I partitioned a 20GB drive into two 7.7GB partitions and the rest swap. My other stuff I kept on a second, 80G drive.

Recently I installed a 500GB drive and now I'm wanting to pitch my smallest drive. I'm hoping I can bump Windows and Ubuntu onto 35GB partitions of the 80GB drive (10GB of swap is enough, yes?). If this is possible could someone give me some help on how? Ubuntu I know I can just reinstall and then copy /home. But I'm really worried about my Windows installation, because I don't have $100+ to spend on a new activation key for a repair install.

---

### Post by aysiu on 2008-08-26
Maybe PartImage?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You can also look into *dd*

**Example**```
sudo dd if=/dev/hda1 of=/dev/hdb1
```

---

### Post by -Zeus- on 2008-08-26
> **aysiu said:**
> Maybe PartImage?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You can also look into *dd*

**Example**```
sudo dd if=/dev/hda1 of=/dev/hdb1
```

where "if" is the partition to copy from and "of" is the destination

---

### Post by Ender305 on 2008-08-26
dd can be dangerous though if you don't do it right, it copies the binary image so it can cause errors etc, I haven't had much experience with it so you should ask someone else first

---

### Post by aysiu on 2008-08-26
> **Ender305 said:**
> dd can be dangerous though if you don't do it right, it copies the binary image so it can cause errors etc, I haven't had much experience with it so you should ask someone else first
It can't really *cause* errors, but it will abort if it encounters errors, which is why *ddrescue* can be handy, too: ```
sudo dd_rescue /dev/hda1 /dev/hdb1
``` But, you're absolutely right. Either one is dangerous if you don't know what you're doing.

---

