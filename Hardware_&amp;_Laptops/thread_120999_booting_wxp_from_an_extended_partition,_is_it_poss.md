---
title: "booting wxp from an extended partition, is it possible?"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by duffman25 on 2006-01-24
Hi

I've recently had to wipe my disk & install everything again. After partitioning the disk, Windows xp is on a extended partition. Can I configure grub to boot it, or wxp needs to be on a primary partition? I'm looking at the grub manual, the section about hiding/unhiding partitions but I'm not sure if that would help me.

I can post my fdisk output later (I'm not at home right now).

Thanxs in advanced, I really don't want to do another reinstall... :(

---

### Post by dsierpin on 2006-01-24
Edit:  My bad

---

### Post by MJN on 2006-01-24
No reason why you can't boot from a logical partition...
 
Check out [http://www.goodells.net/multiboot/]("http://www.goodells.net/multiboot/") - I've not read through it in detail however from first glance it seems to be just the info you need.
 
Mathew

---

### Post by duffman25 on 2006-01-25
[QUOTE=MJN]No reason why you can't boot from a logical partition...
 
Check out [http://www.goodells.net/multiboot/]("http://www.goodells.net/multiboot/") - I've not read through it in detail however from first glance it seems to be just the info you need.
 
Mathew[/QUOTE]

Thanxs for the replys, but I tried fiddling with grub with no success, so I did a backup & reinstalled everything. As a matter of fact, it was dead easy to reinstall linux with a simple tar.gz backup, but XP was really a pain to go through the whole reinstall proces... but that's something people here already know ;)

---

