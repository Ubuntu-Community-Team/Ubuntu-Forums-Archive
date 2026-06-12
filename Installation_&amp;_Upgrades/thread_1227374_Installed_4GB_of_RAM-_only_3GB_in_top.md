---
title: "Installed 4GB of RAM- only 3GB in top"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by birdwin on 2009-07-30
Hello all,

I just installed 2 2GB DDR2-800 modules (I had 2 1GB modules previously). The BIOS and lshw both say that there's 4GB installed, but top says there's 3GB of total memory. What gives? I'm using the integrated Intel GMA3100 graphics chipset, and I'm running 32-bit Jaunty Desktop. Thanks for your time.

---

### Post by philcamlin on 2009-07-30
is it total 3.0 gb or 3.7 or something like that ?

---

### Post by birdwin on 2009-07-30
It says 3086136k total.

---

### Post by philcamlin on 2009-07-30
3086136k KB = 2.87 GB 
are you sure your mobo can handfe 4 gb of ram because its not recognising 1 of them

---

### Post by Nburnes on 2009-07-30
> **philcamlin said:**
> 3086136k KB = 2.87 GB 
are you sure your mobo can handfe 4 gb of ram because its not recognising 1 of them
Or is it just because hes running 32 bit Jaunty?

---

### Post by philcamlin on 2009-07-30
> **Nburnes said:**
> Or is it just because hes running 32 bit Jaunty?

32 bit can handle 4 :)

---

### Post by presence1960 on 2009-07-30
32 bit will not recognize the full 4Gb RAM. Some who are irked by this enable PAE. I hardly think it is worth the trouble. See this [article]("http://www.computing.net/howtos/show/4gb-memory-with-32bit-os/62.html") for an explanation.

here is another :[http://forum.notebookreview.com/showthread.php?t=221094](http://forum.notebookreview.com/showthread.php?t=221094)

---

### Post by Nburnes on 2009-07-30
I'm running the 64 bit Karmic and actually just today I upgraded my RAM to 4 GB and all of it is noticed and working.:popcorn:

Just saying, I think it could be the 32 bit like I stated earlier.

---

### Post by presence1960 on 2009-07-30
> **Nburnes said:**
> 

Just saying, I think it could be the 32 bit like I stated earlier.

+1 You are right on the $$$. That is exactly what is happening. 32 bit whether windows or linux will not recognize 4 GB RAM without PAE enabled!

---

### Post by birdwin on 2009-07-30
Good to know. Any practical differences between Jaunty i386 and AMD64? I've got a Core 2 Duo, so I might as well reinstall.

---

### Post by presence1960 on 2009-07-30
> **birdwin said:**
> Good to know. Any practical differences between Jaunty i386 and AMD64? I've got a Core 2 Duo, so I might as well reinstall.

i would install 64 bit. Flash & java work good now. before doing any updates see this for 64 bit: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

that flash how to works perfectly for me in Hardy, then Intrepid, now jaunty.

---

### Post by Guenter on 2009-09-06
I have Karmic 64bit installed, unfortunately only 3GB are shown:

```
Mem:   3091364k total,  3046212k used,    45152k free,   109488k buffers
Swap:   979956k total,   103464k used,   876492k free,  1944448k cached

```

But 4GB are installed:
```

     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: DIMM 2
             size: 2GiB
             width: 64 bits

```

T60, core2duo t7200, newest bios

---

### Post by ratdude747 on 2009-10-28
running 9.10 64 on a p4 prescott 630... the bios says all 4gb of ram is present (1gb x4), but sysinfo says i only have "2993 MiB". see attachment.

is it me or does that seem off since im using 64.

---

### Post by JBAlaska on 2009-10-28
If any of you have integrated GPU's that would account for some of the missing RAM

---

