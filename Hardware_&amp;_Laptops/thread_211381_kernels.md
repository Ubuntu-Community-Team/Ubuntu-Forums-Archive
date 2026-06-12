---
title: "kernels"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by FrancoNero on 2006-07-08
ok I've done a lot of searching and didn't really find a satisfactory answer, mostly it's opinions.

If I download Ubuntu 6.06 as 386 desktop kernel, will that be good for a fairly recent cpu? I mean 386 seems like a compatibilty compromise, but shouldn't we be at 786 or something right now? I've read somewhere that in order to gain performance one should download a newer faster kernel to replace with the current one.

can somebody clarify the kernel thing and what it is all about?

---

### Post by atoponce on 2006-07-08
There has not been a 786 CPU release.  The latest currently is 686.  You can change kernels easily using Synaptic.

386, 486 and 586 CPU arch's are all Intel Pentium and AMD K5 and earlier.  Anything after that is 686.  786 has yet to be released by any CPU manufacturer.

Ubuntu has chosen to use the 386 kernel for better compatibility with older hardware.  However, all packages that you download from the repositories are optimized for 686, I think.

---

### Post by FrancoNero on 2006-07-08
> **atoponce said:**
> There has not been a 786 CPU release.  The latest currently is 686.  You can change kernels easily using Synaptic.

386, 486 and 586 CPU arch's are all Intel Pentium and AMD K5 and earlier.  Anything after that is 686.  786 has yet to be released by any CPU manufacturer.

Ubuntu has chosen to use the 386 kernel for better compatibility with older hardware.  However, all packages that you download from the repositories are optimized for 686, I think.


so for a first gen. Intel Centrino, would you advise me to upgrad eo a 686 kernel?

---

### Post by atoponce on 2006-07-08
> **FrancoNero said:**
> so for a first gen. Intel Centrino, would you advise me to upgrad eo a 686 kernel? Yes.

---

### Post by Okami on 2006-07-08
I have been wondering about kernels too... My notebook has a AMD Athlon which is around 3 years. What kernel should I use? Right now I am using the k7 kernel.

---

### Post by atoponce on 2006-07-08
> **Okami said:**
> I have been wondering about kernels too... My notebook has a AMD Athlon which is around 3 years. What kernel should I use? Right now I am using the k7 kernel. 686.

---

### Post by Okami on 2006-07-08
> **atoponce said:**
> 686.

Thanks. But why not k7? Or is the k7 kernel for newer amd athlon?

---

### Post by atoponce on 2006-07-08
You can use the k7 kernel.  There is more support and compatibility, I think, for 686 though.  Either kernel will be just fine.

---

### Post by FrancoNero on 2006-07-08
> **atoponce said:**
> Yes.

nice to find that out. why doesn't the ubuntu download page offer that or why isn't there some guide to kernels or something? that would be nice.

---

