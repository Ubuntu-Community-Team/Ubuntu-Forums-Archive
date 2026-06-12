---
title: "Disk space in terms of bytes...gb"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by vrv123 on 2009-02-04
Hi Experts,

This is a question long due, I have ubuntu 8.10 on my dell xps m1330, and thats the only OS on it, so entire partitioned disk is allocated to ubuntu.

I see that the available free/unused disk space is at variance when i compare properties of diskusage analyzer, system monitor & gparted/grub, respectively.

please have a look at the jpg attached to see the storage differences as marked in red.

the extended sda2 and swap sda5 have their own allocations of 8.69 gb each, I feel that is correct. so in reality, I would like to have the unused space of 217.58 in the system, as shown correctly in the gparted.

Can anyone tell me which property should i trust the most,
df command or diskusage analyzer or system monitor or gparted/grub

and why are these tools showing different sizes at the first place ?
is this normal or a bug ?

as a tech guy myself, I would like to see system memory and space allocations to be in sync across the board...

Thanks in advance!

---

### Post by Pumalite on 2009-02-04
There is no bug there. I'd stick to:
```
df -h
```

---

### Post by vrv123 on 2009-02-04
Thanks!

if there is no bug, then why are the numbers different ?

---

