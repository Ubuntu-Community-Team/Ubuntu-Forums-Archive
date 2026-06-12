---
title: "Installation advice on a new system"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by CardPlay3r on 2009-08-17
Hi, I'm pretty new to Ubuntu (couple of weeks I reckon) and my question is related to this system I'd like to buy and install ubuntu on, probably dual-boot with windows vista. It would be say a dual core something with say a 500 GB hard. 

My questions should be read as how to get the best performance for Ubuntu:

1) If it will be a x64 processor, is there any real benefit from installing the 64-bit edition?

2) I've read conflicting opinions about the benefit of using multiple partitions for the various Ubuntu folders, for instance a different partition for /, for /home, for /var and a big one for storage files such as movies etc. 
Does Ubuntu perform better if it has a separate partitions for each of those, instead of having it's own 500 GB partition (or less if I dual boot)?

3) ext4 - faster than ext3, right?

4) How much should the /swap partition be if I have say 2 GB or RAM. What about 4? 2GB is enough for the swap partition right

Thanks looking forward to your answers :)

---

### Post by pmlxuser on 2009-08-17
->if you use 64 bit you benefit the 64 bit facility.
->storing on different partitions is good for data preservation , lets say system files are corrupted if system files and data files are on one partition you are screwd, if on separate partition you just do a clean install and all files data are intact.
->Ext 4 faster -yeah somehow its said on files indexing and things like those haven't noticed the difference yet.
->its recommended that swap be double RAM so yeah 4 GB is OK /you could also use less than that and have a functioning system

---

### Post by CardPlay3r on 2009-08-17
Thanks for the reply. I was asking from the performance point of view, does Ubuntu run faster if it has smaller partitions for each relevant system folder? 

And of course I can benefit from the 64-bit facility, my question is - is there really a performance increase, or most programs still don't run in real 64-bit mode. I also know with windows there are a bunch of problems with 64-bit versions.

---

### Post by CardPlay3r on 2009-08-18
So...anyone? :D one partitions or more, what do you think?

---

### Post by Nburnes on 2009-08-18
I would make:
10 GB / (root) partiton
4 GB swap partition
however many gigs you have left give to /home

---

### Post by CardPlay3r on 2009-08-21
Thanks Nburnes. And I guess another partition for the /home, /var, /bin, /usr etc. folders and perhaps another one for downloads right?

---

### Post by Bartender on 2009-08-21
Nobody's gonna stop you if you want to make dozens of partitions.  I think it's accurate to say that the majority of "average" Linux users don't see much point in going beyond / and /home.

---

