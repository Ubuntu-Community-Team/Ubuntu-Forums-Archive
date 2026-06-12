---
title: "partitioning in Ubuntu"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by Cosmic_Desert on 2005-12-15
Hi there!

How can I partition my disk(50 GB) using the partitioning guide of Ubuntu??
I cant understand how to use the partitioning guide, during the  first installation of Ubuntu :confused: 
I want also a different partition for /home directory

Thanx!

PS: I have a notebook (SONY VAIO - FS135S).

---

### Post by az on 2005-12-15
The partitioner is straightforward, however, if you are not comfortable with the nitty-gritty of partitioning, just take the default and let it figure out the partitions by itself.

You will not have a seperate /home partition, but It is not that hard to backup your /home if youneed to and transplanting a /home partition can sometimes cause a mess anyway.

The only detail you will have to give the installer about partitioning if you take the default is how big to make your new partition.  That's it.  

Be careful.  If your disk has a funny partition table (created by the windows instaler with errors) you will not be able to shrink it - the installer will offer to format your whole drive to install ubuntu on it, in that case.  Just be sure of what it is asking you.

---

