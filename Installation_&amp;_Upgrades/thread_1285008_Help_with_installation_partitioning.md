---
title: "Help with installation partitioning"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by ubuwatson on 2009-10-07
I am familiar with installing Ubuntu, but I am thinking about installing EXT4 this time around - plus as suggested by others I am considering putting my Home directory on a separate partition (any reason not to?).  I have read article after article about how to size everything and what to choose, but I am still confused (different answers all over the web) so I am hoping the community could do it for me.

Laptop (is this safe for EXT4 ?)
Hard Drive: 500 gig
Ram 3 Gigs.


What options do I need to choose (filesystem, size) for each partition (swap, etc).

Thanks

---

### Post by zvacet on 2009-10-08
If you think of fresh install first back up all data/files you don´t want to lose.In install options choose manual way and 

1. root = 10GB                                  ext4   mountpoint     /
2. swap = 1,5-2GB
3.home = rest of free space                     ext4    mountpoint  /home

But put it in this order :root,home,swap

---

### Post by aheckler on 2009-10-08
With 3GB of RAM, I'd only go for 1GB swap, but that's just personal preference I guess.

---

### Post by presence1960 on 2009-10-08
> **aheckler said:**
> With 3GB of RAM, I'd only go for 1GB swap, but that's just personal preference I guess.

if you want to use hibernate you need to make swap the same size as RAM. Because when you hibernate everything you are running is saved from RAM to swap.

---

### Post by pmlxuser on 2009-10-08
with 500GB i would make swap even 4 GB (havent seen my swap in action yet i only have 1GB RAM - but guess because i don't hibernate i prefer shutdown ... yeah no reason yet for this preference)
/ 10 GB reasonable size (havent filled mine with all updates and installtions yet (however if yiou intent to install alot why not make it 20GB

/home 475GB enough....

---

### Post by ubuwatson on 2009-10-08
Thank you all for your help. :KS

---

### Post by ubuwatson on 2009-10-08
after the install i begin receiving kernel panics on boot-up which I have never seen before and I have installed 9.04 on this laptop in the past.  i decided to re-install again, this time using the system defaults and ext3.  i am not sure whether or not ex4 was the problem, but it leaves me pause for concern.

---

