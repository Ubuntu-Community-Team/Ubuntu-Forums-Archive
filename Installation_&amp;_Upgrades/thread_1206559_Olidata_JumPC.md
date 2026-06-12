---
title: "Olidata JumPC"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by mikilion on 2009-07-07
Hello everyone,
I would like to install Ubuntu Netbook Remix 9.04 Jaunty on Olidata JumPC:
[http://www.olidata.com/Prodotti_Vendita/Prodotti/Configurazioni/Scheda_conf.asp?conf=JumPC](http://www.olidata.com/Prodotti_Vendita/Prodotti/Configurazioni/Scheda_conf.asp?conf=JumPC)
The internal disk has a capacity of 2046 MB but the installation requires a partition of at least this size 2097426432 bytes.
I tried installing anyway but, when copying the files, it not succeeded saying that there is not enough space.
This is the output of **sudo fdisk -l**:
```

Disk /dev/sda: 2046 MB, 2046557696 bytes
63 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0xd8135589
```
What solution can I take?

---

### Post by snowpine on 2009-07-07
Can the netbook boot from an SD card? If so, you can install Ubuntu to a 4gb (or larger) SD card.

If you are limited to 2gb, try a smaller distro: Xubuntu, Puppy, SliTaz, etc.

Or, do a minimal install of Ubuntu, then add only the programs you need: [www.psychocats.net/ubuntu/minimal](www.psychocats.net/ubuntu/minimal)
or: [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Good luck!

---

### Post by mikilion on 2009-07-18
Ok, I followed this guide:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
but only installing essentials software I have not even 100 MB free.
I thought to transparent compression filesystem and I found this guide:
[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/)
but it is dated.
Do you what think?

---

### Post by snowpine on 2009-07-18
I think you need a smaller distro, sorry. (SliTaz is my favorite; less than 100mb!)

from [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space 

---

### Post by snowpine on 2009-07-18
ps Also make sure you've chosen Manual Partitioning and installed Ubuntu to a single partition (with no swap). A swap partition would eat up valuable space.

---

### Post by mikilion on 2009-07-18
> **snowpine said:**
> ps Also make sure you've chosen Manual Partitioning and installed Ubuntu to a single partition (with no swap). A swap partition would eat up valuable space.
Yes, sure, I have done so.

I am sorry that can't use UNR but it works just fine on this mini PC.

---

### Post by mikilion on 2009-09-07
Ok, I posted the solution here:
[http://forum.ubuntu-it.org/index.php/topic,301211.msg2391428.html#msg2391428](http://forum.ubuntu-it.org/index.php/topic,301211.msg2391428.html#msg2391428)

---

