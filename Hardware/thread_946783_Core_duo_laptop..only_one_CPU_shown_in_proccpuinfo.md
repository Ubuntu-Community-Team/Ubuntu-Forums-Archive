---
title: "Core duo laptop..only one CPU shown in /proc/cpuinfo + top"
date: 2008-10-13
forum: Hardware
---

### Post by alinux-lb22 on 2008-10-13
Hi
I do have a toshiba laptop it runs dual boot Vista + Ubuntu in vista in the task manager I do see two graphs for the CPU the CPU itself is Duo Core. However in Ubuntu there is only one CPU core in sensors and in /proc/cpuinfo

I did check using adpet and I am using a smp kernel

Linux alinux-laptop 2.6.24-19-386 #1 Wed Aug 20 21:59:50 UTC 2008 i686 GNU/Linux


Please help

---

### Post by PatrickVogeli on 2008-10-13
you are using the 386 kernel. You should be using the generic version. sudo apt-get install linux-generic will take care of installing the kernel and related packages.

---

### Post by alinux-lb22 on 2008-10-13
So would it be correct to say my laptop is currently running on half it's CPU power ?

---

