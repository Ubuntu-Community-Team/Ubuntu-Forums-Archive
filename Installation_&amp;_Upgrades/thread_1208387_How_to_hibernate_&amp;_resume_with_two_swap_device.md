---
title: "How to hibernate &amp; resume with two swap devices?"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by swamytk on 2009-07-09
I am running Ubuntu 9.04 jaunty for my HTPC. 

After installation I am configuring swap partitions. I have two swap partitions of 2GB each (RAM size 4GB) with equal priorities to take advantage of striping by the kernel while swapping. I would like to take this advantage for hibernate/resume also. 

My problem is how to pass ** two ** swap devices (/dev/sda3 & /dev/sdb3) to command line parameter of "resume=.." or resume file in conf.d of initramfs?

---

### Post by prshah on 2009-07-09
> **swamytk said:**
> 
My problem is how to pass ** two ** swap devices (/dev/sda3 & /dev/sdb3) to command line parameter of "resume=.." or resume file in conf.d of initramfs?

In short; you can't. But all is not lost; you can create a swap "file", and use that as a swap area for your hibernation/resume data.

See the manpage of mkswap for details and VERY IMPORTANT caveats; (eg., swap file cannot have "holes"; how to create such a file).

---

### Post by swamytk on 2009-07-10
thanks, prshah.

i have more than enough space to create bigger swap partition to accomodate ram image for hibernation - using only one swap partition for hibernation - both the swap partition for swapping

---

