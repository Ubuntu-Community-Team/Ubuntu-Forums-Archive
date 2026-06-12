---
title: "How to re-add accidentally removed hard drive in RAID5"
date: 2013-06-06
forum: Hardware
---

### Post by chunky56 on 2013-06-06
Hi everyone,

I don't normally post in forums, but I know just enough Ubuntu to get myself in trouble, and I am very worried I have lost my data.

I have a NAS on Ubuntu Server with 4 2TB hard drives in RAID 5. A couple of weeks ago, one of the hard drives died, but my RAID was working, although degraded. Luckily it was still under warranty and I was sent a new hard drive which I installed today. However, when trying to add the new hard drive into the RAID, it was not rebuilding. So I unplugged the hard drive and rebooted the machine. However, I accidentally set one of my OTHER hard drives in the RAID to fail and removed it using mdadm.

Now it says my RAID has two removed hard drives. I still have my 3rd hard drive with all my data still intact, but I don't know how to re-add it back into the RAID array, so it's back to a good (although degraded) state, so I can continue to add the 4th hard drive and rebuild the array. Is it possible to just have Ubuntu realize that the 3rd hard drive has my data and just have it recognized as part of the array again?

When I try to run: sudo mdadm --manage /dev/md127 --re-add /dev/sdd1, it says "mdadm: --re-add for /dev/sdd1 to dev/md127 is not possible.

Please, any help that anyone can give would be much, much appreciated.

---

### Post by SaturnusDJ on 2013-06-06
Can you post the examine output for the drives?
```
mdadm --examine /dev/sd[a-d]
```

Maybe forcing an assemble works (after stopping the array), although I think it's not design to work with drives that have been removed.
```
mdadm --assemble --force /dev/md127 /dev/sd[a-d]
```

---

### Post by chunky56 on 2013-06-06
I think I was able to get it back to a degraded state. I was able to use the mdadm --assemble --force command you suggested and I believe it got it back to a situation where at least 3 out of the 4 drives are working. For anyone in the future who comes across this issue, this is the command I used (assuming the 3 working drives are sdb, sdc, sdd, each with single partitions of sdb1, sdc1, sdd1:

```
sudo mdadm --assemble --force /dev/md127 /dev/sdb1 /dev/sdc1 /dev/sdd1
``` (sudo may not be necessary depending on your situation)

---

