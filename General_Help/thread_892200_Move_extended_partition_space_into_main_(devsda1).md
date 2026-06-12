---
title: "Move extended partition space into main (/dev/sda1)?"
date: 2008-08-16
forum: General Help
---

### Post by catchagato on 2008-08-16
How can I move the extra 3GB in my extended partition (/dev/sda2), into my /dev/sda1? Is it normal to always have that extra partition every time I install Ubuntu Hardy Heron on a "clean" hard drive? I want to just have one big partition with no little extra ones.

---

### Post by p_quarles on 2008-08-16
That's your swap partition. It's most likely too big at present, but you don't want to get rid of it altogether. It depends on how much physical memory you have, as well as how often you use "hibernate" instead of shutting off the computer.

The best way to edit partitions is with a boot disk containing appropriate software. Nearly all Linux live disks have GParted on them, which can be used for this purpose.

---

### Post by catchagato on 2008-08-17
So would you suggest to just leave the /dev/sda2 partition alone? I have 80GB total on my hard drive, and 3GB of memory if that helps. Thanks!

---

### Post by p_quarles on 2008-08-17
If you use hibernate, you should leave the swap partition alone. If not, you can shrink it to something more reasonable (say, 500 MB) whenever you feel like it. Personally, I would leave it like it is to minimize hassle, but there's no reason not to resize it other than the work entailed.

---

