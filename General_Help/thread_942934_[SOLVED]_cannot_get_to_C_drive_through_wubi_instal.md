---
title: "[SOLVED] cannot get to C:\ drive through wubi installed ubuntu 8.04"
date: 2008-10-09
forum: General Help
---

### Post by shift1311 on 2008-10-09
i have two partitions (C: & D: )

i installed ubuntu on my C:\
i can get to my D:\, but not my C:\

the drives show up as Local Disk (thats the D: )
and File System 

im a newb please bear with me for a little while, ill get it soon :(

---

### Post by WWSmith36 on 2008-10-09
open a terminal and post output of this command

```
sudo fdisk -lu
```

---

### Post by shift1311 on 2008-10-09
cornflakes@cornflakes-laptop:~$ sudo fdisk -lu
[sudo] password for cornflakes: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4c6e4c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    57652559    28826248+   7  HPFS/NTFS
/dev/sda2        57652560    78125039    10236240    f  W95 Ext'd (LBA)
/dev/sda5        57652623    78125039    10236208+   7  HPFS/NTFS
cornflakes@cornflakes-laptop:~$ 


thats the output

---

### Post by WWSmith36 on 2008-10-09
Sorry

You are using Wubi so it is automaticly mounted.  Depending of what version of ubuntu you are using you will find windows in the following folder

/host
/media/host

Hope this helps

---

### Post by shift1311 on 2008-10-09
ah
well, thanks all the same, ive found it now!

---

### Post by wowgold119s on 2008-10-12
There are two Bosnians playing for West Ham in an important league match. The ball comes spinning towards them but the captain, who's also well placed to receive the pass, shouts, "Mine!", and both players hit the ground.      ............................................................................................................................................. buy [world of warcraft gold](http://www.mmoinn.com/)| cheap [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)| site: [http://www.mmoinn.com](http://www.mmoinn.com)|cheapest [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)|buy [wow gold](http://www.mmoinn.com)

---

