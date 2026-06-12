---
title: "4GB memory on 32 bit machine"
date: 2010-11-25
forum: Hardware
---

### Post by mydoghasworms on 2010-11-25
A while back, I purchased a laptop with 32 bit processor and 4GB memory.

The laptop came with a sign in the packaging saying that 32 bit OSs report only 2GB of memory, and this seems to be the case.

However, it also seems as if I can only utilize 2GB of memory.

Is that true? Or is there a way to utilize the full 4GB? Why would they sell a 32 bit machine with 4GB memory if you can't use all of it?

---

### Post by garvinrick4 on 2010-11-25
#If Ubuntu in 32 bit recognizes the 4 gig of memory it will install a kernel called:
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda10)" {
#generic-pae makes use of the 4 gig of RAM

---

### Post by Fafler on 2010-11-25
If you run a 32 bit Linux kernel without PAE on a system with 4 gb RAM, you should get around 3.2-3.5 gb avaiable memory detected by the kernel, depending on the chipset and hardware in your system. If you only get 2 gb, there's something else wrong. Try installing memtest86+ and reboot. You will not get a option in your boot menu to run memtest86+. It can tell you exactly what memory modules are detected in your system.

---

### Post by mydoghasworms on 2010-11-25
Thanks garvinrick4, that is exactly it! Thanks for the help!

---

