---
title: "Adding modules"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by Prajna on 2006-11-26
Hi,
 I tried asking this in [http://ubuntuforums.org/showthread.php?t=306878](http://ubuntuforums.org/showthread.php?t=306878) but got no replies (and hardly anyone has even viewed the thread, perhaps the title was too specific).

To put it simply, there is a module I need to add in order to get lm_sensors working on my Dapper machine and I don't know how to go about it.  The module is f71805f and I can, at the very least, get it as f71805f.c and, I guess, compile it, put it somewhere and then install it.

I'm a n00b at ubuntu and have very little linux experience. Could someone please give me some pointers on how to do this.

TIA

---

### Post by zgornel on 2006-11-26
The module is suported by the kernel. Just do a *modprobe f71805f* to load the driver, then run *depmod -a* to redo kernel-module dependencies and then run lmsensors. I do not know if the module exists in the 2.6.15 kernel, I use Edgy and it is in the 2.6.17 kernel. If there is no module, recompile the kernel from scratch.

---

### Post by Prajna on 2006-11-26
It doesn't seem to be in the 2.6.15 kernel, so it looks like I will have to recompile from scratch (or upgrade to Edgy) :(

I had hoped that I might be able to just compile the module and then modprobe it.

Thanks for responding.

---

### Post by zgornel on 2006-11-26
I think there is a way to compile only the module but I never cared about such details ;)

---

