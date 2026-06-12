---
title: "[SOLVED] Can I partition? Previous crashes..."
date: 2008-08-18
forum: General Help
---

### Post by fiddler616 on 2008-08-18
Hey,
The first time I installed Ubuntu, I did a terrible job partitioning--I gave all my free space to Ubuntu, which meant when I tried to install something in Windows there was no space free whatsoever. I ended up reinstalling Ubuntu, and this time gave my / (/home/boot/everything-Linux) partition a measly 5 GB--and now I keep getting low-disk space warnings.
I tried to fix this once, and as I happen to have been booted into Windows, I used the Windows partition manager software, which crashed GRUB (that was actually the reason for the reinstall). I also feel like I read somewhere that you can't just run gparted from Ubuntu because the hard drives are "mounted"--you have to use the Live CD so that they're "unmounted".
FYI, I have four partitions:
C:--Windows (with Windows installed)
D: Windows take two (Programs/documents that didn't fit on C: )
The Ubuntu partition--with everything
A swap partition
So the question is:
Will anything bad happen if I take space away from D:\ and give it to Ubuntu?
And
Will anything bad happen to Windows if I make C:\ bigger? (I don't have a recovery disk, in case you were wondering)
How much do I really need for a swap partition? And finally,
I read on oneandoneis2.org that it's recommended to have separate partitions for / and /home and /boot . Is this true?

Thanks in advance (it's a lot of questions, sorry!).

---

### Post by jazzgossen on 2008-08-18
> **fiddler616 said:**
> Will anything bad happen if I take space away from D:\ and give it to Ubuntu?

No. (Unless your partitioning program does something wrong and messes up the file system, that is.)

> 
And
Will anything bad happen to Windows if I make C:\ bigger?

I don't think so. (The same comment as for the previous question applies too.)

> How much do I really need for a swap partition?
Depends a little on how much RAM you have. I'd say the same amount as your RAM is reasonable. If you want to hibernate, you need at least that amount.

> 
I read on oneandoneis2.org that it's recommended to have separate partitions for / and /home and /boot . Is this true?
Yes, that is good practice, but not necessary. The reason is that if you have keep / and /home separate, you can reinstall Ubuntu, or install another Linux variant to your / partition if you want, and still keep your own files intact.

---

### Post by Elfy on 2008-08-18
If you have a /boot partition please make it big enough and make sure that you keep an eye on what is left before you let kernels update.

---

### Post by fiddler616 on 2008-08-18
Thanks to both of you.
Can I run gparted off of my normal Ubuntu, or should I use the Live CD?

---

### Post by Elfy on 2008-08-18
Use the livecd if you are going to be working on your install partition. If you mena the buntu livecd you will likely need to turn swap off as well if they are both in an extended.

```
sudo swapoff -a
```

You will also need to check that the UUID for both are still the same

```
sudo blkid
```

Check that the UUID for the root drive is the same in menu.lst and fstab

---

### Post by fiddler616 on 2008-08-21
Solved. Thanks, everyone.

---

