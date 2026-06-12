---
title: "duo intel cpu"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by paul foguth on 2007-01-10
with a dual core processor do i use x86 or 64 bit thanks. paul:confused:

---

### Post by zgornel on 2007-01-11
> **paul foguth said:**
> with a dual core processor do i use x86 or 64 bit thanks. paul:confused:

You can use either one depending on the operating system installed.

---

### Post by Dygear on 2007-01-11
> **zgornel said:**
> You can use either one depending on the operating system installed.

He's attempting to choose an OS ...
Core Duo - 32bit.
Core 2 Duo - 64bit.

---

### Post by zgornel on 2007-01-11
Actually, I recommend a 32 bit OS for both proecessors.

---

### Post by RandomJoe on 2007-01-11
> **paul foguth said:**
> with a dual core processor do i use x86 or 64 bit thanks. paul:confused:
You are actually referring to two unrelated aspects of your CPU.

If you have a 64-bit processor, you can use either a 32 or 64 bit OS.  At the moment, I prefer 32 bit for regular desktop use since I just want things to work there.  If I had a second 64-bit system I would probably run a 64-bit OS just for the heckuvit. :)

To fully use a _dual core_ processor you need to use an SMP kernel.  These can be had in either the 32- or 64-bit OS.  If you use a non-SMP kernel, you will only run on one core.  On 6.06/Dapper, the stock kernel is non-SMP, you will have to select the SMP kernel once it is installed.  I'm not running Edgy, so I don't know about it for sure but I would assume it's non-SMP by default as well.

---

### Post by Enverex on 2007-01-11
Speaking for someone with experience on both, STAY WITH 32BIT. I've noticed no differences speed wise, but if you go with 64bit then you'll start having compatability issues with some programs/packages and general frustration with no actual benefits.

---

### Post by penvzila on 2007-01-11
Core Solo = 32bit
Core Duo = 32bit
**Core 2 Duo = 64bit **

---

### Post by penvzila on 2007-01-11
> **RandomJoe said:**
> You are actually referring to two unrelated aspects of your CPU.

If you have a 64-bit processor, you can use either a 32 or 64 bit OS.  At the moment, I prefer 32 bit for regular desktop use since I just want things to work there.  If I had a second 64-bit system I would probably run a 64-bit OS just for the heckuvit. :)

To fully use a _dual core_ processor you need to use an SMP kernel.  These can be had in either the 32- or 64-bit OS.  If you use a non-SMP kernel, you will only run on one core.  On 6.06/Dapper, the stock kernel is non-SMP, you will have to select the SMP kernel once it is installed.  I'm not running Edgy, so I don't know about it for sure but I would assume it's non-SMP by default as well.

I think the default is actually SMP.  I could be wrong, but I'm running an SMP kernel now and I don't remember ever not having both cores.

---

### Post by Enverex on 2007-01-11
Dapper used Non-SMP by default (took me a few days of wondering why it was a bit slow to notice). Edgy uses SMP by default. The "i586" optimisation is a bit worrying though, isn't there a loss of speed from say a K7 option?

---

### Post by penvzila on 2007-01-11
I thought it was all generic now.

---

### Post by tommcd on 2007-01-12
> **penvzila said:**
> I thought it was all generic now.

With Edgy you can use generic or i386 kernel. I have both on my machine. I ended up installing both before I found out  that the generic kernel replaced the 686 and k7 kernels.

---

### Post by Enverex on 2007-01-12
As far as I am aware, "generic" is just a kernel optimized for i586 (uname -a shows that). That means it's not using any of the 686, K7 or other optimizations available in the kernel (basically when you manually compile a kernel you select your processor family from a range). So yes. it is "all generic now" which is probably a bit easier for maintenance, but you are using a less optimized kernel for your processor.

So I ask again, wouldn't there be a performance drop from the previous K7 kernel? (if it didn't make any difference then I doubt the kernel team would implement options for each family of processor in the first place).

---

### Post by zgornel on 2007-01-12
The best way is to recompile the kernel and use the generic as backup in case you screw up something.

---

### Post by Enverex on 2007-01-12
But then what about the third party drivers that Ubuntu uses, or... wait, it doesn't install any by default anyway does it? (other than the nVidia drivers I installed). Heh, I was thinking that if I compiled my own kernel that all the Kernel drivers wouldn't work but it never occured to me that the only modules used other than the nVidia binary I installed are just the kernels own modules which get compiled with the Kernel. Arg, silly me.

---

### Post by tommcd on 2007-01-13
See this for the "straight dope" on the generic kernel:
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

---

