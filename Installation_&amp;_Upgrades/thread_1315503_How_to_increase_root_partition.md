---
title: "How to increase root partition?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by thetechnaddict on 2009-11-05
Hi All...

I'm preparing to upgrade to 9.10 from 9.04 - 

I have the following partitions:

/dev/sda1 ext3 7.48 GiB 5.69 GiB used (boot) - (gets mounted as /)
/dev/sda2 extended 67.05 GiB 
[INDENT]unallocated 5.03 GiB
/dev/sda5 ext3 61.09 GiB 12.89 GiB used - (gets mounted as /home) 
/dev/sda6 linux-swap 956.97 MiB
[/INDENT]

Having cleaned lots of space I still don't have enough to run the upgrade as the root partition is too small.

I am unable to resize that partition - sda1 (it isn't mounted - I'm doing this using gparted on a live disk) - presumably since the unallocated space is on the other partition...

Should I re-install from scratch or is there something I can do to increase the / partition?

Please forgive my errors and correct me!

PS - I have done a backup!

---

### Post by Bucky Ball on 2009-11-05
You are always going to be better off installing from scratch. Don't despair though. Use manual partitioning and just don't format the other partitions, only /

That way /home and whatever partitions you DON'T format (including swap) will remain as was.

Good luck.

*Update: you might also be interested in following this thread. Kinda on the line:

[http://ubuntuforums.org/showthread.php?t=1315484](http://ubuntuforums.org/showthread.php?t=1315484)

ps: not a lot of room to resize for sda1. Where you gonna resize it to? If you don't have free space RIGHT next to the partition you are wanting to resize then you are going to have problems. You need to delete the partition next to it to resize into the free space you have created.

Keep in mind that Ubuntu need not be on a primary partition. You can create one big extended partition covering a whole drive and divide that how you like. You are better starting from scratch because to expand the / partition, you are going to need to delete the extended one next to it, which equates to deleting all the partitions in it.

[QUOTE=thetechnaddict]I am unable to resize that partition - sda1 (it isn't mounted - I'm doing this using gparted on a live disk) - presumably since the unallocated space is on the other partition...[/QUOTE]

It is in the extended one. Get me?

Go from scratch, thetechnaddict

---

### Post by raymondh on 2009-11-05
> **Bucky Ball said:**
> If you don't have free space RIGHT next to the partition you are wanting to resize then you are going to have problems. You need to delete the partition next to it to resize into it.

+1

Also, you need to consider moving the EXTENDED partition first and then root.

Good luck.  back-up.

---

### Post by Bucky Ball on 2009-11-05
> **raymondhenson said:**
> 
Also, you need to consider moving the EXTENDED partition first and then root.


+1

That's it. I keep editing my first post! But that is why you can't access the free space. You would have to delete the extended partition to get to it!

---

### Post by raymondh on 2009-11-05
Following Bucky's line of thinking ..... if you decide to start from scratch, take the opportunity to separate /home from root (/).  That's a BIG help when something like this comes along in the future.

@ Bucky .... LOL

---

### Post by thetechnaddict on 2009-11-05
> **raymondhenson said:**
> Following Bucky's line of thinking ..... if you decide to start from scratch, take the opportunity to separate /home from root (/).  That's a BIG help when something like this comes along in the future.

@ Bucky .... LOL

Oops - I set this up in this way because I was separating / from /home... 

I'm going to go from scratch and first read up some more best practice on partitioning so as to get it right... this time!

Happily I've been doing this long enough to enjoy learning again things I got wrong last time 

Many thanks

---

