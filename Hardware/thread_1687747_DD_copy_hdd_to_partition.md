---
title: "DD copy hdd to partition"
date: 2011-02-14
forum: Hardware
---

### Post by tinkernutfan on 2011-02-14
I may be missing something here but can I use the dd command in this fashion "dd if=/dev/(Hard drive to copy) of=/dev/(partition to copy to) bs=1M" 
 
 
The reason is my windows 7 wont back up (fails) and i need to copy the hd image to another hard drive's partition.
 
 
Thanks ahead. Also i didnt know where to post this.

---

### Post by Kirboosy on 2011-02-14
[COLOR=Red]**Welcome to the Forums!**[/COLOR]

Yes you can use DD to copy from one partition to another. However I would recommend [Clonezilla]("http://clonezilla.org/") because its faster and easier.


Hope that helps.

~Caboose

---

### Post by tinkernutfan on 2011-02-14
> **Caboose885 said:**
> [COLOR=red]**Welcome to the Forums!**[/COLOR]
 
Yes you can use DD to copy from one partition to another. However I would recommend [Clonezilla]("http://clonezilla.org/") because its faster and easier.
 
 
Hope that helps.
 
~Caboose
 
I meant Copy from a hd to a partition (is that what u meant?)

---

### Post by wilee-nilee on 2011-02-14
Besides the dd method you can use gparted to copy a partition to another of the same size, gparted dd's the data.. There is also clonezilla.
[http://clonezilla.org/](http://clonezilla.org/)

I can't confirm the dd you suggest I never use that method.

---

### Post by tinkernutfan on 2011-02-14
> **wilee-nilee said:**
> Besides the dd method you can use gparted to copy a partition to another of the same size, gparted dd's the data.. There is also clonezilla.
[http://clonezilla.org/](http://clonezilla.org/)
 
I can't confirm the dd you suggest I never use that method.
 OK I just dont feel comfortable with clonezilla :confused:

---

### Post by tinkernutfan on 2011-02-14
and this link doesnt have much revelent to this [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

### Post by tinkernutfan on 2011-02-14
&#623;1=sq 1p&#592;/&#652;&#477;p/=&#607;o 0p&#592;/&#652;&#477;p/=&#607;&#305; pp

---

### Post by Kirboosy on 2011-02-14
Give a look at this [page]("http://www.backuphowto.info/linux-backup-hard-disk-clone-dd")

---

### Post by tinkernutfan on 2011-02-14
ty

---

