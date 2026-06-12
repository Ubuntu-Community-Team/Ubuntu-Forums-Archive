---
title: "Fake Raid5 how safe do you think (Ubuntu, Kubuntu)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by attila_66 on 2009-11-08
I want to have data security with my system and decided to have raid 5 system on my pc at home.

I finally setup a raid5 system on Karmic Koala (kubuntu) with 3 160gb hdd's.
I had to setup partitions manually (dont know i made it right but system works).
System is working but performance is not good at all. Hdd led on computer is too much on. Even i am not working on the system (seems there is to much hdd activity).

What experiences you have with ubuntu (kubuntu) fake raid5 systems??

---

### Post by laluz on 2009-11-08
> **attila_66 said:**
> I want to have data security with my system and decided to have raid 5 system on my pc at home.

I finally setup a raid5 system on Karmic Koala (kubuntu) with 3 160gb hdd's.
I had to setup partitions manually (dont know i made it right but system works).
System is working but performance is not good at all. Hdd led on computer is too much on. Even i am not working on the system (seems there is to much hdd activity).

What experiences you have with ubuntu (kubuntu) fake raid5 systems??
"fake raid" is usually used to describe what the motherboard raid is. 
In case you are using mdadm and now hardware raid card it is called software raid not fake raid. 

So which one you have?

---

### Post by Cr0n_J0b on 2009-11-08
if you setup a RAID 5 volume in either the motherboard or with mdadm, you will have to wait for the drives to sych and rebuild.  

type in:  cat /proc/mdstat

if you are using mdadm it will show how far along the rebuild process is.  Once that's done, performance will come back up...but it will not be as fast as RAID 0.  Expect it to be closer to that of a single drive...maybe a little better.

---

### Post by attila_66 on 2009-11-09
Hello,

I dont have raid5 support on my motherborard.
I setup all raid partitions with Kubuntu alternate install CD.
Grub2 loaded to bootsectors of all 3 raid drives. Any of these disk selected as boot device grub2 loads without any problem.


Thank you for the replies.

---

### Post by attila_66 on 2009-11-09
So I waited about 1-2 hours system finished sync rebuild.
But got some errors.
How can I check the health status of the raid partition??

Do you think this system is safe?

---

