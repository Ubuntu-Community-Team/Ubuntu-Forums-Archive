---
title: "Moving hard drive to new machine"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by fortytwo on 2006-08-21
Hey guys,
I just built a new machine, and want to swap my hard drive into it.  The drive is being detected, but I don't think it's under /dev/hda1 anymore, since the boot will begin but then complain that /dev/hda1 doesn't exist, and then it drops me into a simple shell.

What is the easiest way to see what device the hard drive is under, so that way I can just manually change it at the GRUB menu?

Thanks

---

### Post by meng on 2006-08-21
Get some sort of CD that will allow you to boot into Linux. GParted is a reasonable choice, although you could also use any Live CD or at least an install CD that allowed you to drop back out to command prompt.
If using GParted, you'll have a GUI-partition examiner/editor to play around with.
If using something else, you should get to command-line and type cfdisk /dev/hda or fdisk /dev/hda
and if that's no good, fdisk /dev/sda

---

### Post by fortytwo on 2006-08-21
Thanks for the reply,
I tried GParted, and it boots and asks me for any extra boot options, after telling it to skip them, I get:

No GParted cd found!
Kernel panic - not syncing: attempting to kill init!

Have you seen this problem before?  I suppose in the mean time I'll try to find another live cd

Thanks again

EDIT:
Must be something with the machine, I tried another cd and the same thing happened, read it at first, but then complained about the CD being taken out.

Anyway, while the other one was booting, I was able to see that the hard drive was under hdi1, however, after switching the boot line to this, I still have the same problem.

Any ideas?

---

