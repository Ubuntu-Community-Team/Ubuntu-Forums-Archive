---
title: "How to Increase Swap Space"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by kelvinator on 2009-08-03
Today I doubled the ram on my PC from 512MB to 1 GB.
top says I now have 7460980 K of Swap space.

I'm thinking that with more RAM it may be a good idea to increase the SWAP space. Is there a painless way to accomplish this?

---

### Post by merlinus on 2009-08-03
With more RAM you need less swap, unless hibernating.

---

### Post by issih on 2009-08-03
No 1: back up all your important stuff..
No 2: boot from a live cd and start the partition editor
No 3: resize a partition you have empty space in to free space on the disk
No 4: resize/delete and recreate your swap partition to be as big as desired.

Thats about it I think.....

Just be aware that resizing partitions is not a foolproof game so reread No 1 and do it beore messing :)

Hope that helps

---

### Post by kelvinator on 2009-08-03
> **merlinus said:**
> With more RAM you need less swap, unless hibernating.

Thanks - I'll keep it simple and keep things as they are. Apparently resizing partitions is fraught with danger.

---

### Post by running_rabbit07 on 2009-08-03
> **kelvinator said:**
> Thanks - I'll keep it simple and keep things as they are. Apparently resizing partitions is fraught with danger.

I am always playing with my partitions. I have been lucky so far. I do copy my /home to a my file server before each instance though. I have 2 gigs RAM and other than when hibernating I have never seen any files stored on swap.

---

### Post by tabibito on 2009-08-04
Also don't forget to edit your fstab file (/etc/fstab) to match your new swap partition. 

Once, I accidentally format my swap partition and it won't mount again after restart. After a bit of researching, it turned out that the swap partition's UUID before and after being formatted is different. You can get the UUID by using 'vol_id' command in terminal.

```
sudo vol_id [swap_partition]

replace [swap_partition] with your corresponding swap partition, mine is /dev/sda6
```

---

