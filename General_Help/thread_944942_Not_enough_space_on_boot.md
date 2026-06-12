---
title: "Not enough space on /boot"
date: 2008-10-11
forum: General Help
---

### Post by G2k on 2008-10-11
Hey guys, I am currently using Ubuntu 8.10 beta and I've already made a bunch of updates but I can't update the kernel because it tells me that there isn't enough space on my /boot. I tried resizing things with gparted to make my /boot say, 100 MB, but it's a mess and I couldn't do it without shifting around my windows partition, swap partition and creating a new /boot partition. So I was wondering...why do I need so damn much space for a kernel? 50 megs for ONE kernel? I only have 30MB for my /boot since that's how much I used to use for my Gentoo install and I never needed more than like...7 MB. Now Ubuntu is asking for tons more...

I tried taking out the current kernel from boot and placing it on another partition so that I could at least install the new one but the Update Manager told me I still need more space to install the kernel. Does anyone know a workaround for this?

Thanks!

---

### Post by bodhi.zazen on 2008-10-11
I would figure it would be easy to make your boot partition a little larger ...

At any rate, can you use a link ? (if you are you using encryption or LVM ... )

ln -s /path_to_new_kernel /boot/new_kernel

---

### Post by louieb on 2008-10-11
unless you are using an older pc and get a grub error #18,  having a separate /boot partition is as your finding out more trouble than it worth. 

Might just want to copy the /boot files back to /boot in the / (root) partition and do away with the /boot fstab entry.   

Guess you could add the space in the old /boot partition back to the / (root) partition. Or I have found it useful to have a dedicated grub partition. .[IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by hyper_ch on 2008-10-12
100mb for boot is small..

louieb: seperate boot is required for a few things...

---

### Post by Sam on 2008-10-12
> **hyper_ch said:**
> 100mb for boot is small..

No, it's fairly enough. You can easily store 5-6 kernels. As long as you clean up regularly when updates add a new kernel you won't get trouble...

---

