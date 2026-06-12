---
title: "Software RAID: Drive Failure?"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by SupaRice on 2007-01-30
This is probably a reall dumb n00b question, but here it goes:

So, if I setup software RAID between two SATA drives for redundancy on my PC and one of the drives fail.  How will I know?

Also, what commands, utilities, etc are there for monitoring the performance of the RAID setup and the physical drives themselves?

Thanks in advance!

---

### Post by kidders on 2007-01-30
Hi there,

That's certainly _not_ a dumb question ... it's important to know these things!

Here's a quick snippet from a Ubuntu box I have, with RAID 1 on it.

```
# cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 sda1[1] etherd/e1.0[0]
      995904 blocks [2/2] [UU]
      
unused devices: <none>
```

The **[UU]** indicates both devices are alive. /proc/mdstat is a pseudofile that lets you take a peek at what the kernel is doing. It doesn't have much to say, because ... well ... not much is happening.

```
# sudo mdadm --detail /dev/md0
Password:
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Jan 23 07:31:29 2007
     Raid Level : raid1
     Array Size : 995904 (972.73 MiB 1019.81 MB)
    Device Size : 995904 (972.73 MiB 1019.81 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jan 30 23:32:41 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 02e4e04e:131692e3:c78019dc:22e888bf
         Events : 0.3816

    Number   Major   Minor   RaidDevice State
       0     152      256        0      active sync   /dev/etherd/e1.0
       1       8        1        1      active sync   /dev/sda1
```
mdadm is useful for a little more detail. You can also use it to manage arrays, play around with failed devices, etc.

I hope that helps. I posted all the output (rather than just the commands themselves) so you can see how easy/hard it is to make sense of. Post back if it's just gibberish to you!

---

### Post by SupaRice on 2007-01-30
That's exactly what I was looking for, thanks!

You :guitar:

---

### Post by kidders on 2007-01-31
Hehe! :-)

---

