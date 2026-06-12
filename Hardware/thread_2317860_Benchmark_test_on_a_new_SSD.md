---
title: "Benchmark test on a new SSD"
date: 2016-03-20
forum: Hardware
---

### Post by alexpag on 2016-03-20
Hello guys need some help with a new ssd (sandisk ultra II 240gb) in my laptop. I cannot run the benchmark test through Disks. I´ m getting this error:

Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 32: umount: /: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
 (udisks-error-quark, 14)

Any thoughts?

P.S:My distro is ubuntu mate 15.10 64-bit

---

### Post by 1clue on 2016-03-20
If it's your boot disk then you can't unmount it.

---

### Post by alexpag on 2016-03-20
> **1clue said:**
> If it's your boot disk then you can't unmount it.

It is my boot disk. Can I boot a live usb stick unmount the ssd and then run the benchmark test?

---

### Post by 1clue on 2016-03-20
Yes, but be careful that the test is not destructive.  Some tests will destroy data on the disk. If you don't care about th edata then it's no big deal.

---

