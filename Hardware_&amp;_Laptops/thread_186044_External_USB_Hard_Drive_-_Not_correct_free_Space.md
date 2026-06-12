---
title: "External USB Hard Drive - Not correct free Space"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by R4z0r on 2006-06-01
Hello,

I have bought a Medion external usb drive, 250gb. When plug it in with Win XP, there is 240gb free space. When i use ubuntu and mount it, there is only 10gb of free space. There are some folders like "recycled" and "System Volume Info.."

Can anyone help me? How can i get the full 240gb with ubuntu. I use the Live cd v6.06

Thx in advance

---

### Post by tUrtleAE86 on 2006-06-02
That's odd...

When I mount my Windows XP partition in Dapper, 'df' shows that i have only 16kB used, and the rest as free space.

But, it's a 30 GB partition with about 1GB free space, actually.

---

### Post by Bloged on 2006-06-02
Good day everybody.

I don't know if it really belongs here.

Yesterday I installed Ubuntu Dapper 6.06 LTS using LVM partitions like this (from the top of my head so it could be a bit off):
**sda 120Gb total**
15 Gb      /
1.5 Gb     LVM
104.5 Gb LVM
**sda 300.1Gb total**
300.1Gb LVM

Using LVM set this to
1.5 Gb as swap
104.5 GB + 300.1 Gb = 404.6Gb as /home

All went smooth until I checked my free space in Nautilus which show
"4 items, free space: 353.5Gb"
Ok where did thos 52Gb go to... it's to big to be a result of the 1000 / 1024 problem.

So I checked free space using df:
```

Filesystem                                1K-blocks      Used        Available       Use%   Mounted on
/dev/mapper/home-home         390759092  271776     370637896   1%       /home

```
or better formatted using df -h
```

/dev/mapper/home-home         373G            266M        354G             1%      /home

```
Now I wonder since when is 373.000Mb - 266Mb = 354.000Mb? Anyone any answers? Or should I file this as a bug?

Thanks in advance,

Bloged

p.s. 373Gb could be consistent with the partition of ~400Gb given the 1000 / 1024 calculation differences.

---

### Post by Dunlop on 2006-09-20
Has anyone figured anything out about this yet? I'm having the same problem and its driving me bonkers. I can't find anything on any other forums or sites that remedy this.

---

