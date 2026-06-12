---
title: "what to do with internal 8Gb SSD drive?"
date: 2012-03-24
forum: Hardware
---

### Post by miatawnt2b on 2012-03-24
I have a new samsung laptop that has 8Gb internal SSD. In windows this is used as sort of a caching partition to give similar performance to having a solid state drive.

Needless to say I don't use windows, and I am wondering what to use this internal SSD for. My initial thought is to make it swap, but figured I'd ask if anyone has better ideas?

-J

---

### Post by miatawnt2b on 2012-03-26
bump

---

### Post by mastablasta on 2012-03-26
needless to say for anyone to help you, you would need to tell the configuration of your laptop.
 
is SSD the only drive? or is it additional drive? 
 
you could put the whole root and swap on it (depends for what you are using the linux for and how many additional applicaitons you plan to install). If it has 4 GB ram using 8GB hard disk for it might be a waste of space.

---

### Post by Mark Phelps on 2012-03-26
> **miatawnt2b said:**
> ... In windows this is used as sort of a caching partition to give similar performance to having a solid state drive. 

Only in some, specific cases, does that actually help.

Saw a review today of a 50GB SSD -- and even with a drive that big, even then, only in SOME cases did it help with performance gains.  When it came down to sequential reads and writes, it provided no performance improvement.

---

### Post by rmil on 2012-03-26
I guess that you have soldered SSD (irremovable disk) on the motherboard
Personally I would install Ubuntu to the main root directory / on ssd and everything else (spare disk) mount additionaly to separate folder such as /media/disk1. Also if you need swap, I would make swapfile not through partition.

---

### Post by mastablasta on 2012-03-27
> **rmil said:**
> I guess that you have soldered SSD (irremovable disk) on the motherboard
Personally I would install Ubuntu to the main root directory / on ssd and everything else (spare disk) mount additionaly to separate folder such as /media/disk1. Also if you need swap, I would make swapfile not through partition.
 
 
it could also be there is a hybrid disk inside.
 
how would you make swapfile in linux and why is this not the default option if it is better?

---

### Post by Grenage on 2012-03-27
I've not seen a laptop with such, but it could well be used for Intel's SRT, which is an excellent feature.  I'd put as much of the install as possible on it, if you're using it only for Nix.

---

### Post by rmil on 2012-03-27
This is just my opinion. Linux is very adjustable system. It is not possible to take into account every kind of solution. You have specific demand hence something specific was recommended.

SSD is very fast disk so it is wise to use it for installation of file system and necessary software. 
If you have enough RAM swap is not so necessary to exist hence I leave it as option to be adjustable file. Anyway I would not make additional partition because it is wasting of fixed space on small disk.

If I am wrong and SSD disk is the part of some larger disk as cash. Than other ideas might be better. Anyway it is very strange and dangerous to give someone access to ssd as cash inside the larger disk. Cash is Smart memory and used only for its purpose.

Instructions for making swapfile are here:[http://www.ivankristianto.com/os/ubuntu/howto-make-swap-file-in-ubuntu/1156/](http://www.ivankristianto.com/os/ubuntu/howto-make-swap-file-in-ubuntu/1156/)

---

### Post by rmil on 2012-03-27
> **Mark Phelps said:**
> Only in some, specific cases, does that actually help.

Saw a review today of a 50GB SSD -- and even with a drive that big, even then, only in SOME cases did it help with performance gains.  When it came down to sequential reads and writes, it provided no performance improvement.

You should know that tests are ordered mostly as marketing tool to promote one/several products. Also the tests are made for short period of time on one OS with specific software.

For me only live experience from users and friends is considered seriously.
I have changed recently one WD hdd 160GB with Kingston 32GB SSD. 
Speeds and Performances are not comparable. It is true that You must have at least SATAII to feel difference in performance but If you have sata3 then SSD is must have solution

---

### Post by Grenage on 2012-03-27
> **rmil said:**
> It is true that You must have at least SATAII to feel difference in performance but If you have sata3 then SSD is must have solution

I believe Mark was comparing caching (Intel SRT) and sequential data transfers - and he's quite correct.

---

### Post by Mark Phelps on 2012-03-27
> **Grenage said:**
> I believe Mark was comparing caching (Intel SRT) and sequential data transfers - and he's quite correct.

Sorry ... should have made that qualification clearer.  

The article I read specifically explored the Pros and Cons of using an SDD purely for _caching_ -- and, as can be expected, they got mixed results.

---

