---
title: "Performance penalty for 64GB HIGHMEM kernel?"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by anodos on 2006-01-26
I'm using the 32-bit kernel: 2.6.15-12-k7 #1 SMP PREEMPT.
I have 4 GB of memory on my system (Athlon 64 X2 4400+ on nForce4 based motherboard) - however, this kernel only sees about 3 GB of memory.  I'm guessing I have to enable 64GB HIGHMEM support to see it all (since I already have 4GB HIGHMEM support enabled).  However, I'm wondering if there is a performance penalty for enabling 64GB HIGHMEM support?  If someone could enlighten me or at least point me to a useful article I'd really appreciate it (googling has turned up very interesting articles that talk about Linux 32-bit memory management and performance penalties for the 4/4 GB kernel, but they never mention if this is the same as the 64GB HIGHMEM option).
Oh, and yes, the 64-bit kernel can see all my memory, and, no, I would rather not run the 64-bit kernel at this point as I need some things that don't work yet on the 64-bit kernel.
[-o< 
Thanks,
  Anodos

---

### Post by Ocxic on 2006-01-26
I thought that there was a way to run the 64-bit kernel with 32-bit support?

---

### Post by anodos on 2006-01-27
I'm pretty sure you're right... except when it comes to plugins (firefox plugins, etc).  Couple that with proprietary software that has no source code to recompile, and you have a problem.

  - Anodos

---

