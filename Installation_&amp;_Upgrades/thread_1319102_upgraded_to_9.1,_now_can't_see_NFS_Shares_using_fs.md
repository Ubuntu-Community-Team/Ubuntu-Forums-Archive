---
title: "upgraded to 9.1, now can't see NFS Shares using fstab"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by darrude on 2009-11-08
Hi,

I hope this is the correct area to post this.

I have upgraded from 9,04 to 9.10 and now I can't mount my NFS shares on reboot, but it works fine using "sudo mount".

I have tried doing a clean install and my main PC and still it doesn't work.

The line I added to fstab was:

192.168.1.100:/Qmultimedia /mnt/Qmultimedia nfs users,rsize=8192,wsize8192,timeo
=14,intr

I have triple checked all the basic's and everything seems fine.  

Do I need to do it differently on 9.1.

Many Thanks,

Darren

---

