---
title: "partition setup question need confirmation."
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by vedek on 2009-08-13
Hi guys.

I am getting rid of windows completely go me. 

no i am thinking about setting up my hd like this 

ext3/home 138gig
ext3/ 20gig   ----- root partition
swap 2gig

is 20gigbig enough for the root partition and i have checked this out properly

the home partition is going to be all my files etc
the root partition is only for system files 

i am hoping that if i want to experiment then i just install it in the root partition and the home will have all my old files.

if this is wrong then or if you can suggest something else then that would be great

---

### Post by zvacet on 2009-08-13
Yes 20GB is enough (and more then that) for root.When you install make root first then home and swap at the end.This is not only way but for me it seams more natural.

---

### Post by raymondh on 2009-08-13
20GB for root is OK.   I have 20 but even with all my apps, I only have about 8GB filled.

When you experiment, do you want to experiment with other distros?  If so, then a /data might be better than a /home.  See [Bodhi's HOW TO]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition") and his brief explanation on the matter (/data as opposed to /home).  It's under 'options'.

If you plan to stay with Ubuntu and just experiment with versions, then /home will be OK.  Note that it will retain config files, settings, etc. but (at the most) you still have to do minor cosmetic work after a root re-do.

Good luck.

Raymond

---

### Post by presence1960 on 2009-08-13
I used to use a separate /home partition but got away from it because I like trying other distros. I went to data partitions. I still back up my home directory so I have all my config files should i need to restore them or if I reinstall.

There really is no wrong choice. As you use Ubuntu you will come to see what best suits your computing needs.

---

### Post by vedek on 2009-08-14
i have decided thati will have the root home then swap as i will mainly be using virtual box for any distro makes it easier

---

### Post by raymondh on 2009-08-14
> **vedek said:**
> i have decided thati will have the root home then swap as i will mainly be using virtual box for any distro makes it easier

Excellent.  Happy Ubuntu-ing.

---

### Post by vedek on 2009-08-14
well fellas what can i say i am fully intergrated as a ubuntu user. gone are the days of blue screen, device errors and windows error messages that need a degree in cryptography to figure out.

the point is do i regret the decision? 

NOPE

---

### Post by fela on 2009-08-14
Before my 750GB HDD had a head crash, I had a whole 100GB / partition! And 300GB for /home. 20GB should be fine for / (and indeed the whole system depending on what you do with it). It all depends on what programs you install and how many. Right now I'm coping with 30GB for my whole system as everything had to be migrated to my spare 250GB HDD after the head crash.

Yes, winblows is taking up the other 200GB...it has to go but I have lots of games and software on it such as Adobe master collection CS4.

I might salvage an old disk to put winblows on.

---

### Post by presence1960 on 2009-08-14
> **vedek said:**
> well fellas what can i say i am fully intergrated as a ubuntu user. gone are the days of blue screen, device errors and windows error messages that need a degree in cryptography to figure out.

the point is do i regret the decision? 

NOPE

Great! Enjoy Ubuntu.

---

