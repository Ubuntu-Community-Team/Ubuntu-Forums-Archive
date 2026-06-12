---
title: "hard drive errors, how do I fix?"
date: 2009-07-31
forum: Hardware
---

### Post by rhythmiccycle on 2009-07-31
hello,
i've been having a lot of issues with my computer lately.
I decided to reinstall the o.s. hoping that would fix the problem.
i removed all the partitions, and tried to install ubuntu, but i get an error (i think I/O error 5), 

(right now i'm running off the liveCD)

I think the problem is with the hard drive. 

i would just like to completely wipe out the hard drive and make it like new. but i don't know how.

if there are some physically damaged  sectors, is there a was to just partition around those bad parts?

please help

---

### Post by lykwydchykyn on 2009-07-31
> **rhythmiccycle said:**
> hello,
i've been having a lot of issues with my computer lately.
I decided to reinstall the o.s. hoping that would fix the problem.
i removed all the partitions, and tried to install ubuntu, but i get an error (i think I/O error 5), 

(right now i'm running off the liveCD)

I think the problem is with the hard drive. 

i would just like to completely wipe out the hard drive and make it like new. but i don't know how.

filling the drive with zeros should suffice.  You can do this from a terminal on the live CD with the following command:
```

sudo dd if=/dev/zero of=/dev/sda

```
> 
if there are some physically damaged  sectors, is there a was to just partition around those bad parts?

please help

I don't know if the graphical partitioner has the option, but the format command (mkfs.ext3) should take a "-c" switch that will skip bad sectors.  It takes longer because it has to scan the drive.

IME a drive with bad sectors is usually a drive that will soon have more bad sectors.  I'd run "badblocks -v /dev/sda" to see how extensive the damage is.

---

### Post by rhythmiccycle on 2009-08-02
thanks for your help,

it turns out, the problem was with the CD-ROM not the HD.

i changed it, and now everything is installing fine

---

