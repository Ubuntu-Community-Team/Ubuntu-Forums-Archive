---
title: "High CPU usage in virtualbox after 2.6.28-16 kernel"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jalor@yousee.dk on 2009-10-29
Hi

My ubuntu just recently upgraded itsef to kernel 2.6.28-16. And ever since then, virtualbox 3.0.8 is using one full cpu constantly even when the guest operating system is idle.

This problem was not present on kernel 2.6.28-15 (and i have verified it). So I have reverted to 2.6.28-15 for now.

This is a 64bit ubuntu system, triple core AMD. When virtualbox runs in kernel 2.6.28-15, and the guest is idle, cpu usage is a couple of percent (<5%). With kernel 2.6.26-16, cpu usage is 30-40% (corresponding to approximately 1 full cpu in my triple-core system).

Best regards,
Jacob

---

### Post by cnbiz850 on 2009-10-29
This has been discussed somewhere.  Run VBox as follows solves the problem for now.
taskset -c 0 VirtualBox

---

### Post by cnbiz850 on 2009-10-29
This has been discussed somewhere.  Run VBox as follows solves the problem for now.
taskset -c 0 VirtualBox

---

### Post by wareagle on 2009-11-13
I am having the same problem and that does not fix it, however, [this]("http://ubuntuforums.org/showpost.php?p=7235479&postcount=17") does.

---

