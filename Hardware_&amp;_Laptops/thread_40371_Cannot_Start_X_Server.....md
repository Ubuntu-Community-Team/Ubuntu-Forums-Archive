---
title: "Cannot Start X Server...."
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by ghostfacepenguin on 2005-06-08
Ok...I did it...I installed the SMP 686 kernel for dual processor support, now I can't get X server to start. I tried to configure manually with 
It didn't succeed. I get the same message after rebooting. 

I am in desperate need of help, as now my machine is hosed and I don't knowwhat to do next, short of re-installing Ubuntu.

PLEASE HELP!!!!

Thanks,

---

### Post by netrattler on 2005-06-08
Did you install the linux-restricted-modules-686, from your shell prompt just type this and see if it corrects your problem.

sudo apt-get install linux-restricted-modules-686-smp
and reboot your computer.

Joe

---

