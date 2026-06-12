---
title: "64 or 32 bit?"
date: 2008-07-11
forum: General Help
---

### Post by albonatto on 2008-07-11
I bougth a laptop Acer Aspire 5920 and installed ubuntu 8.04. I thougth it was a 32 bit pc but I type: 

uname -a

and the result is: 

Linux Themis 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

This means that I bougth a 64 bit laptop? I am almost sure that the answer is yes but I need a confirmation.

---

### Post by kevmitch on 2008-07-11
Yeah, I'm pretty sure you wouldn't get that response from a 32 bit processor. You would not get past grub with that kernel if it didn't support 64 bits. I think that model comes with a Core 2 which supports the EMT64 instruction set. This is Intel's implementation of AMD64. 

I don't think you can buy a new non-64-bit processor these days.

---

### Post by albonatto on 2008-07-11
Thank you!!

---

