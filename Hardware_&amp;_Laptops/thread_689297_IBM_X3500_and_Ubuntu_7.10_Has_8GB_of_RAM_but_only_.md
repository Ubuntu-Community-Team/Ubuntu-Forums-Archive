---
title: "IBM X3500 and Ubuntu 7.10 Has 8GB of RAM but only shows 3GB's."
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by louish on 2008-02-06
Hi all,

I have a IBM X3500 (7977) server with 8GB of Ram.   Upon boot up, BIOS shows 8GB's.  But the OS (Ubuntu 7.10) only shows 3.1GB's.  The Current kernel running is listed below.  I'm wondering if there is a limit on what Ubuntu see's by default, and if that is the case, how can I change (if I can) that!


Linux 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007

Regards

Louis

---

### Post by Aslund on 2008-02-06
Are sure sure you have taken the 64-bit version and not the 32-bit? 32-bit is limited to 3-3½GB RAM.

---

### Post by /home on 2008-02-06
You have to install the 64bit ubuntu kernel

---

### Post by louish on 2008-02-06
Does this mean a re-install of Ubuntu?  Or just heading to synaptic and installing the 64bit kernel and depends?

L

---

### Post by roaldz on 2008-02-06
> **louish said:**
> Does this mean a re-install of Ubuntu?  Or just heading to synaptic and installing the 64bit kernel and depends?

L

Since the kernel handles memory, you should at least install a 64-bit kernel. Why not 64-bit binaries? You don't have much to lose (because it's stable).

---

### Post by louish on 2008-02-06
When I look to see what I have installed, below is what is listed.


Linux kernel headers for version 2.6.22 on x86/x86_64
Linux kernel image for version 2.6.22 on x86/x86_64

Does this not mean that it is the 64bit version?  Or am I wrong here?

---

### Post by roaldz on 2008-02-07
> **louish said:**
> When I look to see what I have installed, below is what is listed.


Linux kernel headers for version 2.6.22 on x86/x86_64
Linux kernel image for version 2.6.22 on x86/x86_64

Does this not mean that it is the 64bit version?  Or am I wrong here?

You can see it quickly using the "uname" command. Please post the output of "uname -a"
Mine is:
```

roald@roald-laptop:~$ uname -a
Linux roald-laptop 2.6.22-14-rt #1 SMP PREEMPT RT Fri Feb 1 00:55:45 UTC 2008 x86_64 GNU/Linux
```
As you can see the RT (realtime) 64-bit version.

---

