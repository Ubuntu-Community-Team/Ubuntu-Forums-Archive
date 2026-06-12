---
title: "Partition help"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by EvilBro on 2009-04-10
I've been running a dual boot Windows XP/Ubuntu for some time now and recently came to the conclusion that I don't actually use the Windows XP installation. On top of that, when I upgraded to 8.10, the upgrading software said my ubuntu partition didn't have enough space (which I resolved by deleting a few games). 

With 9.04 coming along any day now (well... not any day) I have formulated the following plan: wipe my HD clean and start anew with 9.04. This will involve me having to pick a decent layout for my partitions. I have read that it is smart to create a partition for the OS and a partition for /home (but correct me if I am wrong) as this will allow you to start for scratch more easily in the future. What I have been unable to determine is what would be appropriate sizes.

I have an 80GB HD. At the moment 10GB is reserved for ubuntu. This is apparently too small. What size do you recommend? (20GB or so? which would leave ~60GB for data)

---

### Post by Herman on 2009-04-10
> I have read that it is smart to create a partition for the OS and a partition for /home (but correct me if I am wrong) as this will allow you to start for scratch more easily in the future. What I have been unable to determine is what would be appropriate sizes.Wrong, it's better to install in just one single partition, folders always automatically stretch to whatever size you need, whereas partitions form a rigid barrier.

There's no advantage to dividing your hard drive up into several partitions, it's just a waste of good hard disk space, you need to have backups on some other media anyway.

I even like making my swap in a swap file instead of a separate partition. [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k

That's only my opinion, I'm sure you'll have a lot of people who will say the opposite, and I seem to be representing a minority, (possibly I'm alone, but that's my opinion and I'm sticking to it). LOL!

Regards, Herman :)

---

### Post by u-foka on 2009-04-10
Hy!

I understand Hermann's arguments, but you have to consider other things too... the opinion of people may varry a lot becuse of their different view and habits. We can only point you interessing things to you can make your decision.

So in my point of view:

Swap file pro:
You can change the size of your swap after the installation relatively easy.
Swap file con:
The swap file has a fixed size like a swap partition, so you can't save the space of an unused swap if you use swap files...
If you using swap files, your system have to write the data trough an additional layer (the filesystem) and because of this, the swap partition's performance is better.
If you increase your swap file's size (recreate it) on a havily used filesystem, it may result in a fragmanted swap file.

One big filesystem:
You can use every bit of your relatively small hdd.
Separate home:
I'd like to reinstall my system instead of upgrading from one release to another, this is my habit ;) I've sucked a lot with upgrade on earlier versions, I know people upgraded their systems without problems, so again: you have to choose :p
But with a separate partition for your home, you can easily reinstall your system for any reason, and after all you have to do is to install your applications -what is pretty easy with apt- and your app settings are safe in your home, and ready to use...
Another thing is if you recreate your system filesystem every six month (ubuntu release cycle) you can decreese fragmentation of it, because it has all the fast changing information, like log files, caches, temp, etc...
(I'm using a memory filesystem for temp, but I have a lot of ram ;))

The sizes...
I have a pretty large hdd (320 gb) and it's not a pain if I have 10 gb of it unused on the system side... so my system partition is set to 30 gb, what more than enough for me, with a lot of apps, complete lamp environment for testing, etc... I usually have a least 8 gb free on it..

Well, many people says that Linux is about choices... So what I can advise: Make yours :) and bee happy with this freedom ;)

---

