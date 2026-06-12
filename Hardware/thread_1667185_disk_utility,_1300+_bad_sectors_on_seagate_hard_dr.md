---
title: "disk utility, 1300+ bad sectors on seagate hard drive"
date: 2011-01-14
forum: Hardware
---

### Post by b666 on 2011-01-14
hi, i've got a newish seagate internal hard drive, a couple months old. i just noticed it has 1,300+ bad sectors, according to the disk utilty. it rises about a dozen bad sectors every day, since i first noticed last week. i downloaded seatools, from the seagate website, and have run both the windows version and dos version and they don't report any errors at all! i did the long and short tests with seatools.

what do you think? is this a case of 'false positive' from the ubuntu app? or is my drive dying on me? i dunno what to think,.. *nervous*

---

### Post by quixote on 2011-01-15
Yeah, I'd be nervous too ;)

Given that two out of three say no problem, I'd just check it regularly, and make regular backups.  Which ubuntu disk utility did you use?

---

### Post by b666 on 2011-01-16
i'm using ubuntu 10.10, and used the one in 'administration' called "disk utility". i never tried looking for other ubuntu ones, but i will now.

---

### Post by quixote on 2011-01-16
That's the one called Palimpset, right?  I've used that one a bit to check disk usage and it seems pretty good.  There's also a command line utility called testdisk which is tops for resolving filesystem and partition table problems, but I'm not sure how good it is at physical disk issues.  You can get it via synaptic if the multiverse repository is enabled.  (I think that's the one.  Not sure.)

---

