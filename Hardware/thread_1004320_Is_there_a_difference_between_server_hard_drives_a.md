---
title: "Is there a difference between server hard drives and normal ones?"
date: 2008-12-07
forum: Hardware
---

### Post by Brimfulof on 2008-12-07
Hi, I'm trying to set up my first Ubuntu server.  I hoping to run Zimbra for my work on it, once I had a bit of a play to get it working.

I've found a nice cheap server (HP ProLiant ML110 G5 - Xeon), but I want to get some extra SATA hard drives so I can have RAID.  I can get some well-rated, cheap Maxtor/Seagate drives for £30 each, or ones that are three times as much but claim to be specifically for servers (HP made).

As we're a small charity I'm looking to save money, but I don't want to save a little bit now and have the drives failing in a few months.

Does anyone have any advice or experience of using desktop hard drives in a (mail) server?

Thanks for your help.

---

### Post by dynamethod on 2008-12-07
> **Brimfulof said:**
> **I can get some well-rated, cheap Maxtor/Seagate drives for £30 each**

You can have cheap and maybe speed, but you cant have quality.

You can have quality and speed, but you cant have it cheap.

---

### Post by Brimfulof on 2008-12-07
Thanks for the quick reply dynamethod.

Do you have any specific recommendations, e.g. brands or specific drives?

---

### Post by Stephen_at on 2008-12-07
I thought HP just encapsulated other companies drives in their own cages with modified firmware to support their hotswapping and other things like that.

---

### Post by twright on 2008-12-07
Basically the cheaper a hard drive is the more likely it is to fail (an over simplification but usually true); if you have a RAID setup then the point is to introduce redundancy so that if one of the drives fail you just need to buy a new one as the data will be safe. It should be safe to use cheaper hard drives as long as you have a good RAID setup. I would actually recommend open solaris for such a setup because of the excellent RAID capacities of the ZFS filesystem. 
Remember that redundancy is no replacement for regular offsite backups; one power surge could fry all of your hard drives so you should have a copy of the data as well.

---

### Post by Brimfulof on 2008-12-07
Good point, the last drive I took out of an HP was a Seagate anyway.  As it won't be hot-swappable it shouldn't need any special firmware.  I was just trying to find out if there was any qualitative difference between drives that are intended for servers and those that are just sold for general use. Does one need greater fault tolerance on a server?  Is there greatly increased load between a mail server and a workstation?

Thanks to all for your help on this, I'm liking Ubuntu already, and I've not even installed it!

---

