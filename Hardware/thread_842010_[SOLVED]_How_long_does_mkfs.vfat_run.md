---
title: "[SOLVED] How long does mkfs.vfat run?"
date: 2008-06-26
forum: Hardware
---

### Post by dbsoundman on 2008-06-26
I'm running mkfs.vfat right now to check and label a 200GB IDE drive in an external firewire enclosure and it's taking forever. I started it like 2 hours ago and it's still running strong checking blocks. I'm into the 150 millions now. I'm just wondering if I did something wrong or if this just runs for days before it's done. Here's the code I put in to start the sequence:

```
dan@dan-laptop:~$ sudo mkfs.vfat -c -v -I -n BRANDESKY20 -F 32 /dev/sdb

```

Also, the computer I'm running it on is my laptop, it has an intel core duo at 2.0GHz and 1GB of RAM if that makes any difference.

Thanks,
Dan

---

### Post by dbsoundman on 2008-06-27
So of course not 5 minutes after this post, it finished. Problem solved.

-Dan

---

