---
title: "New Ubuntu installation and file system"
date: 2005-01-11
forum: Installation &amp; Upgrades
---

### Post by marcadams on 2005-01-11
HI;

I have just bought a new PC, and in a few days will be loading Ubuntu onto it.
Although I have been experimenting with Ubuntu for a few months, could someone please reccommend:

1) Which file system should I use (I will be using Ubuntu to learn and program Java). I understand Reiserfs is fairly stable, yet fast for programming tasks??

2) Which parts of my file system should I make into separate partitions? I assume "/home" - but should areas of high file manipulation also be in separate partitions E..g "/tmp" and "/var"??

3) For arguement's sake, say I have a 40 gb hard drive, roughly how much should I allocate to the separate paritions?


Thanks in advance,
Marc

---

### Post by wallijonn on 2005-01-11
The first question to ask is, "How much of linux do I want to reserve disk space for?"

If the answer is "all" then making the whole HD for Linux and accepting the Ubuntu defaults should suffice to get a system up and running. 

The next question should be (just as it is in Windows), "Do I want to have a separate partition just for my data or used as a backup area for my data so that I can just re-install the OS if it blows up?"

If that is the case, then the next question is, "How much data do I expect to save on my HD?" If you are working with video you might want to reserve 50% of the disk space, if lots of music files then 25%, for lots of documents and spreadsheets, then 20% isn't unreasonable, etc. 

You would then create two partitions, one for the OS and one for DATA. 

But Ubuntu, like most new distros, doesn't really need separate partitions for a desktop where only one disk is likely to be used.

In the server world it is another matter, as you'll want to keep your /var files on a separate disk so that if the /var "partition" (actually the separate disk) gets full it doesn't crash the server. Likewise you're very likely to have separate disks just for user accounts and their data. You'd have a whole disk just for the OS and maybe another disk for applications. If your server is also doing double duty for email or the web then you'd have separate disks for those functions.

For a desktop, partitioning is superfluous. It is much better to accept the defaults and readily be able to get the system running than to have to work with remappings of directories and creating hard and soft links throughout.

---

### Post by az on 2005-01-11
Unless you are running a server that runs full-tilt, you will not really notice a difference in performance using one filesystem over another.  Ext3 is probably used more than reiserfs.

---

### Post by marcadams on 2005-01-13
Thanks for the feedback.

So for my desktop environment, it looks like I might as well stick with the most stable 'Ext' file system as I will not get any benefit from choosing anything else.

As for the partitions, would it not be a good idea to at least have the '/home' on a separate partition, so the OS can be wiped (and upgraded) - but the docs, emails, configurations etc can be left alone?

thanks
Marc

---

### Post by mip on 2005-01-13
[QUOTE=marcadams]As for the partitions, would it not be a good idea to at least have the '/home' on a separate partition, so the OS can be wiped (and upgraded) - but the docs, emails, configurations etc can be left alone?[/QUOTE]

Yes. IMO.

---

