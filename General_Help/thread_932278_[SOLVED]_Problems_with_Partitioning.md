---
title: "[SOLVED] Problems with Partitioning"
date: 2008-09-28
forum: General Help
---

### Post by Otustelija on 2008-09-28
I'm moving around a couple of partitions to be able to expand one of them. Because one of the partitions to be moved is the Ubuntu partition, I'm doing this from a Live environment (Ubuntu 8.04 64-bit) using GParted.

The total process consists of four operations, three of which went fine. Now the fourth (expanding a FAT32 partition to the left) has been going on for about an hour and a half. The "Applying pending operations" is doing the operation "Grow /dev/sda7 from 151.97 GiB to 249.64 GiB -> move filesystem to the left" and has shown "4.74 GiB of 4.74 copied (00:00 remaining)" for over an hour.

How can I find out if the program is still trying to complete and accessing the HD?

---

### Post by Otustelija on 2008-09-28
After another 30 minutes the situation is still the same. ```
sudo hdparm -C /dev/sda
``` returns:

```
/dev/sda:
 drive state is:  active/idle
```

Should I take it that it is still being used by GParted as no volumes are mounted and the drive is not sleeping/standby?

I don't think it should take this long even if it is moving the whole 150 GiB... but I'd rather not destroy my data just yet. Any ideas?

---

### Post by -Zeus- on 2008-09-28
well, this is a bad situation you are in.  I'd let it run overnight at least, but let someone else here let you know the safest way to stop it when it doesn't stop.

---

### Post by Otustelija on 2008-09-28
> **-Zeus- said:**
> well, this is a bad situation you are in.  I'd let it run overnight at least, but let someone else here let you know the safest way to stop it when it doesn't stop.

I'd rather not wait too long, because I still have some work to do this night and I need access to my files.

I noticed under details that "move filesystem to the left" is "using libparted". I guess that's due to FAT32 format - the earlier moves used "internal algorithm". Could this be a reason for poor reporting (00:00 remaining) and for the whole thing taking so long? Moving a 50 GiB filesystem (in step 2) took 30 minutes, but that was using the "internal algorithm".

---

### Post by Otustelija on 2008-09-28
Yes! I was just about to cancel, when the command finished. Apparently when GParted uses libparted for partition management a)reporting is off and b)operations take over 2x as long as with the internal algorithm. Good to know!

---

