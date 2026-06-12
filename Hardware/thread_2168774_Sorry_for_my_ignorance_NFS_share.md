---
title: "Sorry for my ignorance NFS share"
date: 2013-08-19
forum: Hardware
---

### Post by albertramsbottom on 2013-08-19
We have two web servers and these need to both access an NFS share (recommended for the application), and im a bit in the dark about the NFS share

We plan to have a set of discs in raid 5 configuration.  Can I directly mount these disks using NFS to both web servers? or do I need a separate server as an NFS server?

Cheers for any help

---

### Post by TheFu on 2013-08-19
> **albertramsbottom said:**
> We have two web servers and these need to both access an NFS share (recommended for the application), and im a bit in the dark about the NFS share

We plan to have a set of discs in raid 5 configuration.  Can I directly mount these disks using NFS to both web servers? or do I need a separate server as an NFS server?

Cheers for any help

[http://www.onlamp.com/pub/a/bsd/2002/02/14/big_scary_daemons.html](http://www.onlamp.com/pub/a/bsd/2002/02/14/big_scary_daemons.html) should help.
While you **can** share storage from 1 computer to another via NFS and it will work just fine, if you are trying to get HA or any sort of redundancy from the server setup, then you really want a separate NAS/SAN ... e.i. storage sits on a different device than any web/app/DB server.  In this way, clustering can be used to failover from srv-A to srv-B.

As far as NFS is concerned, the RAID happens at a different level - NFS doesn't know or care.  The RAID would be configured at a lower level on whatever machine the disks connect ... er ... there are exceptions if you use iSCSI or AoE storage (very recommended BTW), but if you plan to use NFS, I wouldn't use iSCSI or AoE storage too ... well, not on a small budget (less than $50k).

Does this make any sense?  Only had a few sips of tea this morning - brain not fully working yet.

---

### Post by papibe on 2013-08-19
Hi albertramsbottom.

Here's a good place to start: [Setting Up NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

In a typical LAN you set up one NFS server that shares one or more NFS exports, and several clients machines can mount the same share.

Regards.

---

### Post by albertramsbottom on 2013-08-19
Yes the data storage needs to be on a separate storage solution and using this solution we do not need clustering, both web servers just read and write to the share.  Session affinity is taken care of by the load balancer and session data is stored in the shared data folder. I think in my ignorance then we do need an extra server set up as a NFS file server that is connected to a RAID 5 array of disks

Me thinks

---

### Post by TheFu on 2013-08-19
> **albertramsbottom said:**
> Yes the data storage needs to be on a separate storage solution and using this solution we do not need clustering, both web servers just read and write to the share.  Session affinity is taken care of by the load balancer and session data is stored in the shared data folder. I think in my ignorance then we do need an extra server set up as a NFS file server that is connected to a RAID 5 array of disks

Me thinks

Clustering may be needed ... if there is a DB server involved and high-availability is desired. Having two DB servers read/write from the same DB on an NFS mount **would be bad.**  This applies even for SQLite.  If there isn't a DB involved and only static files are there, file locking can cause a deadlock when both client systems attempt to write to the same file.  If the server app is well-written, that shouldn't happen.

Anyway, there are thousands of different configurations possible based on the information the OP provided. We just don't know. Of course, there are just a few "best practices", but that wasn't the question.  
* "Do I need"
* "Would it be best if"
are very different questions after all.

Anyway, without knowing the application architecture, transaction rates, volumes, HA requirements, and lots of other things, it is hard to make any "best practice" recommendations. If there is $zero budget, that also feeds into the recommendations.

---

### Post by albertramsbottom on 2013-08-19
No DB clustering needed at this stage and its not the db that writes to the NFS share, just cache, session data and actual files uploaded to the application such as pdf files and video files.  Basically the application recommends using an NFS share to store the data.  Just need to know that we will require a 4th server to configure it as an NFS file server

---

### Post by TheFu on 2013-08-19
> **albertramsbottom said:**
> No DB clustering needed at this stage and its not the db that writes to the NFS share, just cache, session data and actual files uploaded to the application such as pdf files and video files.  Basically the application recommends using an NFS share to store the data.  Just need to know that we will require a 4th server to configure it as an NFS file server

"require" is a strong term. You do not "require" another server to be an NFS box.  There are lots of ways to have NFS and you don't necessarily even need a regular server.  Lots of RAID storage boxes provide NFS as any option. That might be the way you'd prefer to go.  If you are a small business, a dedicated storage machine/device can be highly cost effective. [http://www.smallnetbuilder.com/nas](http://www.smallnetbuilder.com/nas) will show some options.

If you are a larger business ... Dell, HP, IBM, Oracle, Hitachi, EMC make storage solutions too, at a price.

You haven't mentioned the amount of data to be stored. [http://openstoragepod.org/](http://openstoragepod.org/) is a DIY option based on the Backblaze design.

Of course, you could also add another server and connect storage to it and need to maintain, patch, troubleshoot, ... etc. that box too. This method would provide greater flexibility than any dedicated storage box.

Again, lots of options.

---

