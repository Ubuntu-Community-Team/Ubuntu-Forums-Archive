---
title: "Raid filesystem"
date: 2011-03-12
forum: Hardware
---

### Post by Jagoly on 2011-03-12
Hi. I'm eventually going to be building an ubuntu-running htpc. I really want fast boot times. I don't want to go for an ssd, because the $perGB is just too low. So I have decided to go for two hdd's in a raid. I will probably go for raid 0. I don't care in the slightest about backup, because everything will be on several other pc's aswell. I only need about 600gb, and I haven't picked the disks yet because it will still be a while before I build. What filesystem works good with a raid? I have heard that I should use xfs.

Also, what sort of read performance would raid 1 give in comparison?

---

### Post by Jagoly on 2011-03-13
Is this the right place to put this?

Edit: whoops I just noticed that it was already moved to the appropriate place. I put it in gaming and leisure because I didn't want to clog up one of the busiest sub-forums there is. Now I've just double posted there. Sorry.

---

### Post by cascade9 on 2011-03-13
A small SSD will be enough, you only need a few GB for root. A decent SSD should be faster than a RAID0 setup as well. 

RAID1 will be slower than RAID0. It would actually be slower than a single disc....

---

### Post by Jagoly on 2011-03-13
> **cascade9 said:**
> A small SSD will be enough, you only need a few GB for root. A decent SSD should be faster than a RAID0 setup as well. 

RAID1 will be slower than RAID0. It would actually be slower than a single disc....

problem is price. SSD's are expensive. I'd get one if I could afford it, but even sub-30gb disks are above $100. I need a minimum of 600gb and I don't want to spend over $120 for the storage.

PS: For pure read performance (not "snappyness"), would raid1 be faster than 1 disk? I have no intention of using raid1 (waste of a disk). this is just out of curiosity.

---

### Post by cascade9 on 2011-03-13
> **Jagoly said:**
> problem is price. SSD's are expensive. I'd get one if I could afford it, but even sub-30gb disks are above $100. I need a minimum of 600gb and I don't want to spend over $120 for the storage.

Possibly looking in the wrong place? 

Kingston 30GB SSD V-series, $79- 
[http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=159&bid=2&sid=57717](http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=159&bid=2&sid=57717)

That + a 1TB drive would give you much better bootup speeds than 2x the same 1TB drives in RAID0. 

Not that is covers boot speed, but this is worth reading- 

[http://www.anandtech.com/show/2739](http://www.anandtech.com/show/2739)

[http://www.anandtech.com/show/2217](http://www.anandtech.com/show/2217)

I've got nothing against RAID, and RAID5/6 I have a lot of respect for, but I think that people overestimate how much RAID could help in some situations. This case (bootup speed) is one of the cases where people do overestimate any gains.....a lot.  

> **Jagoly said:**
> PS: For pure read performance (not "snappyness"), would raid1 be faster than 1 disk? I have no intention of using raid1 (waste of a disk). this is just out of curiosity.

RAID1 is slower than a single disc. (well, if you run a nice hardware controller with a big chunk of cache you might write to the cache faster, but apart from that RAID1 is slower).

---

### Post by Jagoly on 2011-03-13
> **cascade9 said:**
> Possibly looking in the wrong place? 

Kingston 30GB SSD V-series, $79- 
[http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=159&bid=2&sid=57717](http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=159&bid=2&sid=57717)

That + a 1TB drive would give you much better bootup speeds than 2x the same 1TB drives in RAID0. 

Not that is covers boot speed, but this is worth reading- 

[http://www.anandtech.com/show/2739](http://www.anandtech.com/show/2739)

[http://www.anandtech.com/show/2217](http://www.anandtech.com/show/2217)

I've got nothing against RAID, and RAID5/6 I have a lot of respect for, but I think that people overestimate how much RAID could help in some situations. This case (bootup speed) is one of the cases where people do overestimate any gains.....a lot.  

RAID1 is slower than a single disc. (well, if you run a nice hardware controller with a big chunk of cache you might write to the cache faster, but apart from that RAID1 is slower).

Whoa... I DEFINITELY was. I might look into that one.

But what about TRIM or similer? To my knowledge, that's the tech that stops SSD's from slowing down or dying after a while. It only works on NTFS. Not sure how reliable my knowledge is though.

---

### Post by cascade9 on 2011-03-23
> **Jagoly said:**
> But what about TRIM or similer? To my knowledge, that's the tech that stops SSD's from slowing down or dying after a while. It only works on NTFS. Not sure how reliable my knowledge is though.

TRIM has been in the linux kernel since 2.6.28 , and 'full support' since 2.6.33. 

Provided that you are running 2.6.33 or higher, you dont need to worry about TRIM at all.

---

### Post by Jagoly on 2011-03-24
> **cascade9 said:**
> TRIM has been in the linux kernel since 2.6.28 , and 'full support' since 2.6.33. 

Provided that you are running 2.6.33 or higher, you dont need to worry about TRIM at all.

Cool! The forum (corsair) info I had was very outdated.

Anyway, if anyone can suggest a good fs for raid, that would be good. I will use an SSD now (thanks to cascade9), but for people googling for this we should put it here.

Thanks again!

---

