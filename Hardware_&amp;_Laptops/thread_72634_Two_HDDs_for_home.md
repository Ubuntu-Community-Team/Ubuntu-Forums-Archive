---
title: "Two HDDs for /home"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by Sykil on 2005-10-06
I just got a shiny new Maxtor DiamondMax 10 250 GB from Newegg. At the moment, I have a 120 GB disk for /home and a 36 GB for /. Would it be possible for me to use both the 250 GB and the 120 GB for my /home partition? (I know about RAID, but my disks are different sizes, as you can see).

BTW: I want to use XFS for /home, if that helps anything.

---

### Post by landotter on 2005-10-06
I don't know about xfs, but mounting one of the drives as /home/Sykil/hdb would be a piece of cake. In breezy use the disk management tool under System--Administration

---

### Post by Sykil on 2005-10-06
Oh! I wasn't aware that I could do that. My plan was to wait until Breezy to install it anyway, so this could work out fine.

Thanks for your reply. :)

---

### Post by deBaas on 2005-10-06
I have a 80 gig disk for /, swap and windows and two 200 gig disks for /home. I use LVM wich works great. See [lvm howto](http://tldp.org/HOWTO/LVM-HOWTO/) for more info.

---

