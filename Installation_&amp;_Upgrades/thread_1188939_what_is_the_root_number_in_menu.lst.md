---
title: "what is the root number in menu.lst"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Gatemaze on 2009-06-16
What does the root=UUID=<some cryptic number> (example below). Is it some kind of ID of the partition? or hard disk maybe? and where can I find it? It seems hex too.

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9ca91394-af94-4a9d-aae3-b90d6c79d0b4 ro splash

Cheers

---

### Post by VastOne on 2009-06-16
> **Gatemaze said:**
> What does the root=UUID=<some cryptic number> (example below). Is it some kind of ID of the partition? or hard disk maybe? and where can I find it? It seems hex too.

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9ca91394-af94-4a9d-aae3-b90d6c79d0b4 ro splash

Cheers

A Universally Unique Identifier (UUID) is an identifier standard used in software construction, standardized by the Open Software Foundation (OSF) as part of the Distributed Computing Environment (DCE). The intent of UUIDs is to enable distributed systems to uniquely identify information without significant central coordination. Thus, anyone can create a UUID and use it to identify something with reasonable confidence that the identifier will never be unintentionally used by anyone for anything else. Information labeled with UUIDs can therefore be later combined into a single database without needing to resolve name conflicts.

(Thank you Wiki)

The great thing about this in Ubuntu is that all drives are identified by the UUID making multiple boot scenarios easy to manage.  I have several images of my systems on different drives for testing and with UUID I can easily make sure that each finds the right environment when booting to them because you can change the UUID for each drive. So when I create an image, I cannot keep the original UUID or I would have conflicts, so I change it and make the menu.lst and fstab changes accordingly.

---

### Post by Gatemaze on 2009-06-16
Thanks. Well explained :)

---

### Post by VastOne on 2009-06-16
> **Gatemaze said:**
> Thanks. Well explained :)

Thank you...

Also, blkid is the command from term to show you all of your UUID's and you can use tune2fs -U random /dev/whatever if you ever need to change it.

---

