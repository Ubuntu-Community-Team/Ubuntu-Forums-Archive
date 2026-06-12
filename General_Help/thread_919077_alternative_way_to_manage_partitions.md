---
title: "alternative way to manage partitions?"
date: 2008-09-13
forum: General Help
---

### Post by grashdur on 2008-09-13
I want to transfer from wubi to a regular install with LVPM. First I need to create partitions. I followed the instructions at Sourceforge, but when I tried to start up the Partition Manager, I got

> root (hd1,)
Error 21: Selected disk does not exist.

Though I suppose I could learn to find and rewrite the Partition Manager, I think it will be faster and easier to just do a fresh install of HH. But this gives me an idea: :cool:

Can I use the partition manager that's built into the Ubuntu installation disk, and then just exit from the installation utility at that point, get back into Ubuntu and use my new partitions for LVPM? 

I intend to also create a separate partition this time for /home -- and I'm not even sure whether LVPM supports such an option.

---

### Post by grashdur on 2008-09-20
I could not boot up the installation disk from my DVD/CD drive, as I kept getting that same error message each time I tried to Install, or Run Live CD. 

I have a workaround: I'll just continue to rely on Wubi for now, and check each new Ubuntu version to see whether it can boot up its installation disk on my drive.

---

### Post by ago on 2008-09-21
hd(1,) means that it is looking for it in the second HD... So you might want to adjust the grub/grub4dos entry

---

### Post by grashdur on 2008-09-22
That sounds good. I figured it must be just a matter of specifying the drive. How do I find that file and do that? 

(Will that be on the Ubuntu installation disk -- so that I need to copy, edit, and then re-burn it?)

---

