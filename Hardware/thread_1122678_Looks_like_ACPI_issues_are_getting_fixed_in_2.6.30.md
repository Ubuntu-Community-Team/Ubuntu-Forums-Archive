---
title: "Looks like ACPI issues are getting fixed in 2.6.30"
date: 2009-04-11
forum: Hardware
---

### Post by mpadams on 2009-04-11
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc1/)

I was tracking down a solution for the problem where ACPI spams syslog and messages every 6 seconds with a fan notification, and noticed that an RC build for 2.6.30 is up. I loaded it up on my x64 Jaunty box and the ACPI spamming seems to have stopped. Any of you with ACPI problems may want to install this kernel and see if they go away.

---

### Post by kenfeyl on 2009-04-27
I'd like to try 2.6.30, but after installing the three modules (headers amd64, headers all, image amd64) on my Gateway M-6827 Core 2 Duo laptop, the kernel throws the following error on boot:

modprobe: FATAL: Could not load /lib/modules/2.6.30-020630rc1-generic/modules.dep

I've checked and the file is there, however. I've also installed all previous kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) without problem. Any ideas?

---

