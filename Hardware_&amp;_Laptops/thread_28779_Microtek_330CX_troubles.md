---
title: "Microtek 330CX troubles"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by fat_larry on 2005-04-21
Hey there.  I'm told this Parallel scanner should work under Linux, but the Sane page is rubbish and confusing (ok, unfair, I'm getting a little frustrated tho) and all the help it can give me is "Try the backend for your scanner", with absolutely no mention of how this is done!

I know that the microtek2 backend will do the job, I know I have a parallel port scanner, and here is the output from dmesg | less:

```

parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).

```

Who can help me with my next step?  XSane only recognises my TV card, not my scanner.  sane-find-scanner doesn't do what it says on the tin.  

xsane microtek2:/dev/lp0  just fails

 ](*,) 

Cheers

---

