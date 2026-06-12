---
title: "Ubuntu won't install where i want"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Ranek on 2009-02-11
Hey


I have 2 Hard Disks a 320gb Samsung with Windows XP home installed and a 160gb WD with 2 partitions, 1 of which is currently running Windows 7 and the other is empty.

This is my first time installing Ubuntu and i'm getting a problem. When starting the installation and choosing where i want to install i can either create a new partition on the Hard Disk running Windows XP. Or i can take over the whole of the 160gb WD HD.

But ideally i would like to be able to install Ubuntu on the 2nd Parition of my 2nd HD and dual boot it.

I'm sure this is probably a mistake i am making, could anyone enlighten me with a solution.

Thanks

Chris

---

### Post by 73ckn797 on 2009-02-11
When you get to the partitioning part of the installation, have you selected manual and designated where you want it installed?

---

### Post by Ranek on 2009-02-11
I didn't select Manual because i was worried that it might just start formatting something that i didn't wanted to.

If i choose Manual will it allow me to select an already designated partition on my hard disk?

---

### Post by oldos2er on 2009-02-11
> **Ranek said:**
> I didn't select Manual because i was worried that it might just start formatting something that i didn't wanted to.

If i choose Manual will it allow me to select an already designated partition on my hard disk?

 Yes, you need to use 'manual' if you want to point Ubuntu to a specific partition.

---

### Post by 73ckn797 on 2009-02-11
> **Ranek said:**
> I didn't select Manual because i was worried that it might just start formatting something that i didn't wanted to.

If i choose Manual will it allow me to select an already designated partition on my hard disk?


Yes.

Possible that you will see the 2nd drive with the 2 partitions listed as "sdb1 & sdb2". If Windows 7 is on sdb1 then you want to select sdb2 as the partition for Ubuntu. The program will take care of the rest from there.

---

### Post by Ranek on 2009-02-12
I went to manual put i still can't really select the partition to install to. I can resize partitions etc. But i'm not sure how to actually select the one i want to install on.

I'm sure i'm probably just missing something small :(

---

### Post by 73ckn797 on 2009-02-12
Time to do some home work:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html) 

Look around there.

---

