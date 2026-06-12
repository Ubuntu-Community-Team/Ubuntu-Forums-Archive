---
title: "Advice on getting a normal HDD vs a hybrid one, and where are there good benchmarks?"
date: 2013-02-17
forum: Hardware
---

### Post by blackbird34 on 2013-02-17
Hi

I'm currently hesitating as to whether to upgrade my computer to a bigger HDD with hybrid technology or not... Is the difference worthwhile on an average computer?
I'm wondering whether to get this[ 750gb €60 7200 RPM HDD]("http://www.pixmania.com/fr/fr/7057981/art/seagate/disque-dur-interne-moment.html") or this [750gb €100 7200 RPM hybrid]("http://www.pixmania.com/fr/fr/11413401/art/seagate/disque-dur-interne-moment.html") both from the Seagate Momentus brand. Are they good value for money?

Secondly, if I clone my current dual boot system straight on to the new HDD with Clonezilla (which i'd therefore learn to use, but it doesn't look difficult) can I expect it to just boot up and go, or are there complications? Especially, would Win7 and Ubuntu Precise realize straight away they're on a Seagate hybrid hard drive instead of the factory WD drive? Do hybrids have special firmware or something?

Thanks

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by tgalati4 on 2013-02-17
Boot a Live DVD, connect your drives and enumerate them with fdisk, then copy the device:

```
sudo fdisk -l
sudo cp /dev/sda /dev/sdb
```

Use gparted to expand the partition or add partitions on the back of the drive.  If gparted complains about the partition not ending on a cylinder, then allow it to fix it.

Use *blkid* to get the UUID of the new drive.  Edit /etc/fstab and grub to substitute the old UUID with the new UUID so it will boot properly.

Works with WinXP partitions, don't know about Win7.

Keep your old drive as a backup.

---

### Post by offgridguy on 2013-02-17
On a related note, with my most recent laptop, I decided against the hybrid 
hard drive and went with total SSD. One reason ,as already mentioned, the speed
Another perhaps more important, the portability aspect, bumps, knocks etc.

I did have to sacrifice some size, memory wise but i can always connect an external drive if I need more.  So far i am really liking the SSD.

---

### Post by blackbird34 on 2013-02-18
Thanks very much for the advice everyone. I've bookmarked this for when I get my new drive. (I decided against pure SSD because I wanted more than my current 250gb to keep my dual boot and build a nice big music library that was not on an external drive).
Thanks also for the heads up about GParted, means I actually have all the software ready to go without any learning at all :)

---

