---
title: "easy peasy1.1 to netbook remix"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by n1ght28 on 2009-10-11
ok,
so I'm trying to change from Easy Peasy (A distro based on ubuntu 8.04) to UNR and my problem is,

I have a complicated partition setup on my EEE PC 1000he,
I have a triple boot running with OSX, XP and Linux.

OSX sd1
XP sd2
Linux swap sd3
Easy peasy 1.1 sd4
Common storage partition (Fat32) sd5

and a Chameleon bootloader with a beautiful GUI loading the whole three

I have Grub installed on the same partition as Easy Peasy.

What options do I select when installing NBR, specifically the partition menu, I can't seen to figure it out,
also is there definitely an option to install GRUB on the same partition as NBR,

Does anyone also know if there is a chance that the install will mess with the Chameleon boot loader,

Cheers for any help,

If you need any further info please just ask.

thanks again,

---

### Post by Intrepid Ibex on 2009-10-11
Well I didn't quite understand what you mean with "NBR" :/.

If it's a distro (and you didn't mean "MBR"), then it will most likely mess up your MBR with it's own bootloader (e.g. grub).

---

### Post by n1ght28 on 2009-10-12
> **Intrepid Ibex said:**
> Well I didn't quite understand what you mean with "NBR" :/.

by NBR I meant Netbook Remix

when I installed Easy Peasy it gave me the option to install GRUB on the same partition as Easy Peasy which meant that I wouldn't have any problems with it messing with my Bootloader (Chameleon)

Is that option not still available with the Ubuntu Netbook Remix installer, I haven't been able to find it,

---

### Post by Intrepid Ibex on 2009-10-12
I'm not 100% sure, but I _think_ even when selecting to install grub to a partition, a few lines in MBR will be changed to point to that partition (but I'm really not entirely sure).

---

