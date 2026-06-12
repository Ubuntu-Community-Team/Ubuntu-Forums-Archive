---
title: "hard disk"
date: 2008-07-01
forum: Hardware
---

### Post by 0perator on 2008-07-01
i have a hard drive

it is in /media/disk

how do i check what /dev/sd < (letter there) the disk is?

thanks

---

### Post by hardyn on 2008-07-01
don't really understand what you are asking.

/dev/sda refers to the first fixed disk

/dev/sda1 refers to the first partition of the first disk
/dev/sda2 second, first 
...

---

### Post by Odrodzona-Sarmacja on 2008-07-01
> **0perator said:**
> i have a hard drive

it is in /media/disk

how do i check what /dev/sd < (letter there) the disk is?

thanks

You open terminal and type there "mount". It should list all your partitions and their mount points. Look for line with your "/media/disk" in it and then you can read what file system, uuid and /dev/sd_ it has.

Good luck!

---

