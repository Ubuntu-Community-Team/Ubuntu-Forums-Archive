---
title: "LVM + software raid...after adding RAID+1 drive system won't boot"
date: 2008-10-29
forum: General Help
---

### Post by jbwiv on 2008-10-29
Guys,

I had installed Ibex Beta on a machine with one harddrive. Because I knew I eventually wanted to software raid (mirror) the drive with another, I went ahead and partitioned it for software raid, installed LVM on top of it, and was happy. 

A few days ago, I added a new drive to the system. I then booted up, formatted the drive for raid, and added it to the existing RAID device (/dev/md0) as a mirror. Everything went smoothly...it sync'd up just fine and I was cruising.

However, last night I applied apt updates and rebooted...and now it won't come back up. It says something along the lines of "Can't find root=/dev/mapper/LVM_ROOT", which is indeed my root LVM and is specified this way on the grub boot config. I would post exact message, but this happened this morning and I'm at work now. Anyway, it then drops to a busybox session.

I suspect something is happening that prevents md0 from being activated properly. Can you suggest some things I might try to recover the system?

Thanks!
jbwiv

---

### Post by ilrudie on 2008-10-29
I think you need a custom initrd.img in order to boot from lvm volumes.  Some kernel patches were released recently that probably don't include mapper loaded into the initrd.img.  I'd venture to guess this is causing your problem.  
Perhaps try booting into the last kernel version that worked for you and following whatever instructions you used when initially setting up booting into your lvm_root to make a new initrd.img.

---

### Post by jbwiv on 2008-10-29
> **ilrudie said:**
> I think you need a custom initrd.img in order to boot from lvm volumes.  Some kernel patches were released recently that probably don't include mapper loaded into the initrd.img.  I'd venture to guess this is causing your problem.  
Perhaps try booting into the last kernel version that worked for you and following whatever instructions you used when initially setting up booting into your lvm_root to make a new initrd.img.

I agree with you and that was my first thought. However, I went back two kernel versions and no luck. Perhaps I need to go further...will try tonight. Surely Ubuntu kernels are shipping with initrds that support LVM?!

---

### Post by ilrudie on 2008-10-29
I would doubt if ubuntu ships with mapper in the initrd image.  If I recall correctly I had to install modprobe mapper after I installed LVM2 which means its not in the generic kernel... the server kernel may have it though.

I wouldn't bother going back past the last kernel that worked.

---

