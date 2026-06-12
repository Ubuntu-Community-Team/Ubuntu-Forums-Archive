---
title: "Partman failed with exit code 10"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by p0tamus on 2009-06-17
I am trying erase Windows completely on my Acer Veriton S461 desktop, and install Ubuntu 9.10 . During installation , the partition manager stops while scanning disks with the error "Partman failed with exit code 10". 

I have successfully been able to install Ubuntu 9.10 on my laptop, and install openSUSE 11.1 on this Acer Veriton desktop. 

Please help! i can't stand Windows! and i dont want to use openSUSE either. It is not as friendly as Ubuntu for a noob like me.

---

### Post by Mark Phelps on 2009-06-18
Would suggest you download and burn the current GParted LiveCd from distrowatch.com and retry using that.

---

### Post by p0tamus on 2009-06-18
Thanks for the reply Mark, I tried with Gparted Live Cd, created two partitions:
1. Linux-swap 2048MB
2. ext2           70+GB (rest of the drive)

But ubuntu installation still failed with the same error

---

### Post by Mark Phelps on 2009-06-20
Change the ext2 partition to ext3 and try again.

---

### Post by p0tamus on 2009-06-22
I tried with ext3, still same problem. I went ahead and tried and installed Ubuntu 8.04 successfully! dont know why i tried that earlier. 

Later i tried 9.10 again, still the same problem. Is ok i guess, i will stick to 8.04 for a while.

---

