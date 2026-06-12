---
title: "How to dd properly?"
date: 2009-07-08
forum: Hardware
---

### Post by DnDer on 2009-07-08
Server at work that we're repurposing for something new, and I need to blow the drive.

Catch is, on boot Lilo says there are two options. When it defaults to the first and starts booting, I see /dev/hda2 and /dev/hda6. So, that means the hard drive (only a single physical hdd in the server) has been partitioned at least 6 times.

How do I dd the whole thing in one fell swoop? I'll probably use something like like Knoppix, or 9.04 live (if I can find my discs!), instead of doing it from the cli that's already there.

I just want to end up with a single hard drive, with a single partition, all zeroes. Nothing fancy.

---

### Post by az on 2009-07-08
The presence of a partition called sda6 doesn't necessarily mean that it's been partitioned six times.  But that's not really important at this point.

If you want to wipe the partition table, there are many ways to do it.

You could use dd to write zeros to the first block:

(Make sure hda is the proper device!  On a different (read newer) version of Linux, it may be sda...)
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1

You can use cfdisk to delete the partitions and write the empty partition table to the drive:

sudo cfdisk /dev/hda

You can use parted, fdisk, etc....

Beyond clearing the partition table, I doubt you will benefit from zeroing the whole drive.  That will take you a long time and will not bring you any other benefit than creating a new partition and formatting it to whatever new filesystem you want.

---

### Post by DnDer on 2009-07-08
For /dev/zero that you showed me, I said HDA, and forgot to number it. My terminal session froze, but the computer seems like it's working (my processor usage hit the roof) to do what I told it to.

Is there something I can add to the line next time for being able to see time elapsed, time remaining, or maybe just a % done?

---

### Post by DnDer on 2009-07-08
<Scratches head> Doesn't look like I did it right.

```
$ sudo dd if=/dev/zero of=/dev/hda1
dd: writing to `dev/hda1': No space left on device
78165298+0 records in
78165297+0 records out
40020632064 bytes (40 GB) copied, 972.941s, 41.1MB/s
$
```

---

### Post by az on 2009-07-08
Well, you wrote zeros onto hda1 until it reached the end. 

To empty the partition table, you need to write zeros to the first block of the drive, not the first partition.  The first block (boot sector) comes before the beginning of the first partition.

sudo dd if=/dev/zero of=/dev/hda bs=512 count=1

---

### Post by DnDer on 2009-07-09
Oops, sorry. I thought that was an option, not part of the process.

So I need to use the "bs=512 count=1" tag before I run cfdisk?

---

### Post by az on 2009-07-09
> **DnDer said:**
> Oops, sorry. I thought that was an option, not part of the process.

So I need to use the "bs=512 count=1" tag before I run cfdisk?

No.  That's what you need to run if you want to zero out the first block of the drive, which contains the partition table.  Every command-line utility has it's own specific set of options and arguments.  To find out about them, use the man command:

Example:

man dd

---

