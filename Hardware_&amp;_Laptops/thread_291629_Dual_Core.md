---
title: "Dual Core"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by kdub432 on 2006-11-02
Hey everyone.
I'm happy to say my computer is running fine. However, i was just wondering if ubuntu has built in support for dual cores, like my athlon 3800.

---

### Post by kdub432 on 2007-01-17
Usually ubuntuforums are more helpful than this... but 
turns out i was using the wrong kernel. The generic Linux kernel (or the SMP kernel) has built in dual core support. You can tell if your system monitor has two processors listed. (I was using the wrong kernel, and thusly my computer was half as fast as it should have been)

---

### Post by amaab on 2007-01-18
I have the same problem. Used the liveCD and had 2 cpu's in the System Monitor, but when I installed Ubuntu I only have 1. How did you change the Kernel?
I use a AMD Athlon 64X2 4400+.

---

### Post by tronica on 2007-01-18
you need the the generic kernel to have smp support. And just tell grub to use that kernel.

---

### Post by mcduck on 2007-01-18
in dapper (6.06) there's no 'generic' kernel. Instead there are SMP kernels for dualcore CPU's:

For AMD CPUs 'sudo apt-get install linux-k7-smp' and for Intel ones 'sudo apt-get install linux-686-smp'. After that reboot the machine (and make sure you select the new kernel from the Grub menu). If everything is working fine you can uninstall the 386 kernel.

---

