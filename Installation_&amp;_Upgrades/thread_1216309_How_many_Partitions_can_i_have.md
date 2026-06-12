---
title: "How many Partitions can i have"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by ramnarayan on 2009-07-18
Hi

Just got hold of a new HD - 500 Gig,

the main reason i wanted this large size HD is so that i can run multiple Linux OS's. 

So the question is how many partitions can i have and how to make so many happen

My present 80 gig HD has
ntfs - 12 GB
vfat (shared) 3 GB
Extended Partition

/boot 100 mb
swap 3 GB
Ubuntu 9.04 / 7.5 GB
Ubuntu 7.10 / 3.3 GB
Pardus Linux / 3.3 GB
/home - 45 GB

In my recent Ubuntu 9.04 installation - it did not seem to worry too much about this extended partitions, so am curious as to how many partitions can i have on one physical HD

thanks

---

### Post by Elfy on 2009-07-18
4 primaries - one of which can be extended. The extended can have many logicals in it - not sure of the limit.

If you want to install win on it - make the forst a primary then extended for the remainder.

---

### Post by TheNosh on 2009-07-18
> **forestpixie said:**
> 4 primaries - one of which can be extended. The extended can have many logicals in it - [COLOR="Navy"]not sure of the limit.
[/COLOR]
If you want to install win on it - make the forst a primary then extended for the remainder.

more than any sane person ever needed

i'm pretty sure it somehow has to do with your processor and other resources but it's always really high

i read something a while ago on how to multiboot a couple versions of windows along with around 60 or so linux distros (with all the linux distros on logical partitions

---

