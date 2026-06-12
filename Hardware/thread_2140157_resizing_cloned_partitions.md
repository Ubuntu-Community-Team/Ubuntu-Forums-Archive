---
title: "resizing cloned partitions"
date: 2013-04-28
forum: Hardware
---

### Post by kyalami321 on 2013-04-28
So I did a full install of Ubuntu (all default settings) 12.04 to a 40GB drive. I've since cloned the drive (full clone, incl. boot sector, etc.) to a 120GB drive. But now, I've got about 80GB of unused space since the partition sizes were kept the same. 

Can I safely resize the ext4 partition (now ~30GB) using gparted on a livecd, without having to deal with any funkyness? 

Thanks!

---

### Post by ibjsb4 on 2013-04-28
You should be able to do that without problem.  Keep in mind that both share the same UUID so both cannot be plugged in until one is changed.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uuid&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uuid&sa=Search&cof=FORID:9)

---

### Post by ahallubuntu on 2013-04-28
~

---

### Post by kyalami321 on 2013-04-28
thanks for the respnses, guys. luckily the ext4 partition is a logical, separate from the extended partition that has the swap partition inside. will post back if anything goes awry.

---

### Post by ahallubuntu on 2013-04-28
~

---

### Post by kyalami321 on 2013-04-28
correct! my mistake

---

