---
title: "limit ram 32 or 64 bits? Once and for all"
date: 2013-02-05
forum: Hardware
---

### Post by jamn40 on 2013-02-05
i have ubumtu 12.10 ... my uname -a is Linux ubuDev 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:05:29 UTC 2013 i686 i686 i686 GNU/Linux

meaning, 32 bits but i got 8gb ram 

free -m -t

total       usado      livre    compart.  buffers     em cache Mem:          8018       4616       3402          0         47        624
-/+ buffers/cache:       3943       4074
Swap:         3814          0       3814
Total:       11833       4616       7217

SO... am i using fully potential 8gb or this is just wrong ? I read other threads about this subject, but no one answer for sure... 

any lights ? tyadv

---

### Post by howefield on 2013-02-05
Looks like a 32 bit operating system using the PAE kernel enabling use of all your ram.

---

### Post by JayKay3OOO on 2013-02-05
32 bit Linux with PAE should allow up to 64GB RAM to be seen and used.

64 bit Linux has now gained used in some operations so it might be worth using the 64 bit version of Linux.

---

### Post by tgalati4 on 2013-02-05
You will also gain a 10% to 40% increase in speed for specific operations using 64-bit.  There is an extra operation (or 2) to translate the Physical Address Extension (PAE) to fit within the 32-bit (4GB) register address space of the i686 (32-bit) kernel.

And it will always nag you that you can get your system to run just a little bit faster.

---

