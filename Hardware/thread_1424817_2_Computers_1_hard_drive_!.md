---
title: "2 Computers 1 hard drive !"
date: 2010-03-08
forum: Hardware
---

### Post by mnml on 2010-03-08
I have recently tried to use my 64bit Desktop computer hard drive into my 32bit macbook laptop.
For some reasons it worked (I had to struggle a bit in recovery mode to delete the xorg configuration and reboot with X, and everything else working fine..) I was surprised to see it running fine since it's the 64bit edition of ubuntu and the macbook 2,1 is running a intel dual core CPU.
I would like to know if there is any way I can keep both xorg config file without having them interfering on each others. And why the 64bit version still works fine on a 32bit computer?

---

### Post by cascade9 on 2010-03-08
If 64bit runs, its not a 32bit machine. Probably its a Core 2 Duo, and they are all 64bit. The original core series (duo and solo) is 32bit only, but as far as I know all the new intel macs are Core 2 or better. 

No idea on the xorg problem. I dont think is possible, but I could very well be wrong.

---

### Post by mnml on 2010-03-08
> **cascade9 said:**
> If 64bit runs, its not a 32bit machine. Probably its a Core 2 Duo, and they are all 64bit. The original core series (duo and solo) is 32bit only, but as far as I know all the new intel macs are Core 2 or better. 

No idea on the xorg problem. I dont think is possible, but I could very well be wrong.

You Are right, Macbook 2,1 are running Core 2 Duo ... I didn't even know.

---

### Post by efflandt on 2010-03-08
I didn't realize 64-bit would run on my Intel chip laptop from 2006 either until I saw people mentioning it and I tried it from USB.

When I tried to boot 64-bit Ubuntu CD on my desktop at work, which appears to have 2 cpus with hyperthreading, the kernel refused, saying something like it could not run amd64 on i686.

---

