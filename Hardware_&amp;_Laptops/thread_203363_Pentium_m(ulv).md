---
title: "Pentium m(ulv)"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by MrTAZ on 2006-06-25
Hi everybody ;) 

I installed ubuntu dapper on my vaio tx2/hp.
But when i select 686 kernel, computer is slower...?

anyways?

---

### Post by .t. on 2006-06-25
Well, if that's the case I'd suggest running the 386 kernel, or if you are up to it, then recompile (use make-kpkg) with the CPU config setting set to pentium-m. That way you'll get GCC optimizations for your CPU. I've a Pentium M 725, and the -686 seems faster.

---

### Post by MrTAZ on 2006-06-29
i did... (build kernel with pentium-m)
That's bad.
slower than 386 build...

---

### Post by .t. on 2006-06-29
Weird. It shouldn't be. Which kernel are you using? It may be different to mine as I am running on Edgy; however, Edgy's not that different to Dapper at the moment. I can't help any further, but I recommend the Gentoo forums, as the people there are used to fixing and compiling kernels and the like.

---

### Post by MrTAZ on 2006-07-06
Yeah, it shouldn't be...  
I don't tried on a dapper kernel.  
Only on debian kernel...  
But, i tried and that's work fine!  
thx!

---

