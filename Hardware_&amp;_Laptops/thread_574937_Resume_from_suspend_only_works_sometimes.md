---
title: "Resume from suspend only works sometimes"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by 3dmaker on 2007-10-13
Hey guys, Suspend only works sometimes for me. It usually works, but around the third time I suspend and resume, my keyboard and mouse are disabled! Any idea what I can do to fix? I have ATI card, but with the fglrx drivers, nothing works. Plus I only need firefox and open office so I have no use for fglrx. I am on the "ati" driver.

---

### Post by trippinnik on 2007-10-14
I'm having a similar problem with Gutsy.  On Launchpad they ask you to provide this information:
Please include the following additional information, if you have not already done so (pay attention to lspci's additional options), as required by the Ubuntu Kernel Team:
1. Please include the output of the command "uname -a" in your next response. It should be one, long line of text which includes the exact kernel version you're running, as well as the CPU architecture.
2. Please run the command "dmesg > dmesg.log" after a fresh boot and attach the resulting file "dmesg.log" to this bug report.
3. Please run the command "sudo lspci -vvnn > lspci-vvnn.log" and attach the resulting file "lspci-vvnn.log" to this bug report.
4. Please follow this procedure : [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

For your reference, the full description of procedures for kernel-related bug reports is available at [WWW] [http://wiki.ubuntu.com/KernelTeamBugPolicies](http://wiki.ubuntu.com/KernelTeamBugPolicies). Thanks in advance!

from this bug:
[https://bugs.launchpad.net/bugs/134476](https://bugs.launchpad.net/bugs/134476)

---

