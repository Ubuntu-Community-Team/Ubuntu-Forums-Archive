---
title: "Helpless! Kernel Panic during boot unknown block (0,0)"
date: 2008-08-09
forum: General Help
---

### Post by karthikb23 on 2008-08-09
Hi,
I am compiling a Vailla Kernel for 2.6.11.
I have compiled ext2, ext3 lvm, raid and initrd support into my kernel. (As per all suggestions i read while googling).
(I have a Seagate IDE HD.)

But time and again i get the following kernel panic:

"Kernel Panic unable to mount root fs on unknown block (0,0)"

I am really tired of compiling my kernel, about 10 times, and seems aimless now.

Any assistance please??

Thanks in advance.

---

### Post by karthikb23 on 2008-08-10
Hi,
Any suggestions please?
Is there something more i can do to get a more suggestive diagonostic message?

---

### Post by fjgaude on 2008-08-10
I can't really said what to suggest... why are you using such an old kernel? And are you using the latest **md** and **mdadm** modules? There could be some conflict with mixed releases.

---

### Post by karthikb23 on 2008-08-11
Hi,
Well as for an old kernel, yes it is old:)

But sure i can compile it without issues. Afterall someone did build a kernel out of this too right :lolflag: So i want to persist and check what else i can do.

As for your comment:

"And are you using the latest md and mdadm modules? There could be some conflict with mixed releases."

Could you please elaborate? I dint understand...

Thanks a lot for yr input.

As apart, I just thought i may inspect my initrd as well, to see what exactly it is doing, that maybe i am missing out.

Regards!

---

### Post by fjgaude on 2008-08-11
Regarding md and mdadm, there has been many updates to these items since your kernel, and since you activated raid, and if you are using the latest updates to the support programs to Ubuntu, there might be a conflict. Just a thought.

I do know that the latest kernels handle IDE as SATA drives. That's about it for me and ideas. <smile>

Good luck with your adventures.

---

### Post by karthikb23 on 2008-08-11
Thanks!
i'll try something more n see :)

---

### Post by psusi on 2008-08-15
It looks like you don't have an initrd so the kernel is trying to mount the root filesystem directly and failing since it was not built with the correct block device number for the root filesystem hard coded and/or can't parse the root= kernel command line parameter.  I would suggest that you just install the proper Ubuntu kernel package instead of trying to build your own.

---

### Post by karthikb23 on 2008-08-16
Thanks psusi!

But i want to try building my own kernel.

When i build the bzImage, on completion it displays "root block 
(3,7)" but not (0,0).

Could this have something to do with this?

What does this mean (any hints :)?

Thanks again!

---

### Post by psusi on 2008-08-17
You need to use mkinitramfs or update-initramfs to build an initrd and have grub load it with the kernel.

---

### Post by karthikb23 on 2008-08-18
Hi,
The kernel was finally built successfully. I had missed compiling "Generic IDE support", which i located by seeing the modules loaded by my default kernel, after machine boot.

Thanks a lot for the help.

---

