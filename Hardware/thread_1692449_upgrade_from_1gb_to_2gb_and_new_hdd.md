---
title: "upgrade from 1gb to 2gb and new hdd"
date: 2011-02-21
forum: Hardware
---

### Post by LawShadow on 2011-02-21
Hi all,

First my specs:

Amd Athlon 3800+ 2.4ghz
Asus a8n sli deluxe
Corsair 1gb ram (2x 512mb)
Leadtek 6600gt gpu
WD 200gb hdd (ide)
Coolermaster 450w psu

I recently switched from windows xp to ubuntu 10.10. But applets open slowly for example opening ubuntu software center takes about 4 to 5 sec. I noticed a slight decrease of RESPONSIVENES when i open applets, while at my work ubuntu 10.04 i think... is installed with a P4 and 1.5gb ram and is older then my rig and to my suprise everything is more responsive then my pc. Could it be the 1.5gb ram? If i open ubuntu software center it takes 2sec sometimes less, everything works just fine on my own pc.

Will an upgrade from 1gb to 2gb ram increase overall responsiveness wich i can see, i'm not talking about faster boot but more responsiveness in opening applets and a more smooth way of using ubuntu, also upgrading to a new fresh WD hdd (planning for a dual boot first hdd for windows xp second for ubuntu) will the new hdd for ubuntu add to more responsiveness?

Also when i do multiple downloads with rapidshare lets say 15 rar file downloads at the same time i could still use the internet fairly fast on XP. But on ubuntu even after 4 rar files downloading internet usage (browsing) is very slow, how come?

Thanks in advance

---

### Post by LawShadow on 2011-02-22
no one?

---

### Post by khelben1979 on 2011-02-22
More RAM and a faster hard disc will improve the performance because the swap will be used less. Make sure to install the non-free nVidia drivers for maximum performance.

The choice of hard disc is critical if it's used as swap. [StorageReview.com]("http://www.storagereview.com/") has some tests available.

---

### Post by cascade9 on 2011-02-22
> **LawShadow said:**
> Will an upgrade from 1gb to 2gb ram increase overall responsiveness wich i can see, i'm not talking about faster boot but more responsiveness in opening applets and a more smooth way of using ubuntu, also upgrading to a new fresh WD hdd (planning for a dual boot first hdd for windows xp second for ubuntu) will the new hdd for ubuntu add to more responsiveness?

If you arent using almost all of your 1GB, increasing RAM wont help much, if at all. 

As for the new HDD, the closer towards the 1st sector of the drive makes things faster. The closer to the end of the drive, the slower.

BTW, NCQ (native command quing) wont work with nForce4 SLI chipsets and linux (or BSD, etc) from everything I've read. It wont make a huge amount of difference, but it will have some impact f you decide to get a SATA drive.

---

