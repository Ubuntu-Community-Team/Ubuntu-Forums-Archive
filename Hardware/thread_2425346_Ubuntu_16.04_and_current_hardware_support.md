---
title: "Ubuntu 16.04 and current hardware support"
date: 2019-08-24
forum: Hardware
---

### Post by username-already-used on 2019-08-24
Hi,

I am currently working with Ubuntu 16.04 and would like to build a new PC with either an AMD Ryzen 5 2600, an i3-9100 or i5-9400. However, because of some software dependencies (ROS Kinetic) I currently need to stay on Ubuntu 16.04. Therefore I wanted to ask if anybody knows some incompatibilities with current hardware and an older Ubuntu version? Will there likely be any issues or should this be now problem?

Thanks

---

### Post by guiverc on 2019-08-24
You are talking about very recent hardware, but using an OS that came out in 2016-April.  Software is rarely ahead of hardware too, and even using the HWE (hardware enablement stack) the software stack will only approach early 2018.  Yes you may have issues unless it's using chipsets that were already a few years old, but I'm only guessing.

---

### Post by username-already-used on 2019-08-24
Ok, thank you. Would it make a difference if I install (or compile) a newer kernel manually like v5.0 in Ubuntu 16.04 for better hardware support instead of 4.15 from the last HWE?

---

### Post by TheFu on 2019-08-24
I run this:```

~$ inxi -z
CPU~Hexa core AMD **Ryzen 5 2600** Six-Core (-HT-MCP-) speed/max~1410/3850 MHz Kernel~4.15.0-58-generic x86_64 
Up~6 days Mem~11579.0/16033.5MB HDD~1512.3GB(33.0% used) Procs~315 Client~Shell inxi~2.2.35  
```

It is a 16.04.6 install running about 8 virtual machines and nowhere near using the full CPU until I run some video transcoding on it.  Nothing special needed.  Built the box last December.  Asus B450 motherboard.  RAM is 3200 Mhz.  Used the Asus motherboard built-in over-clocking for RAM and the CPU to get the RAM working. The CPU automatic overclock was minor, 6%. No stability issues, though there were some with a kernel in May under extreme loads.  I haven't seen any issues since and none before that time.

Ryzen is by-far the most cost effective CPU choice for a desktop today.

Update:
While I'm happy with the 2600, the 1600 is about 40% less cost and nearly the same performance.  I've seriously considered building a $200 Ryzen 1600 with a cheap Asus MB and 8 GB of RAM for a failover box.  It would replace a Pentium G3258 that is a media server, NFS server and a few other small services like Calibre and running 1 VM.  My 2600 build was about $430 last December. A 1600 build would be just over $200, probably.  Buying 3 yr old stuff really saves the cash.

---

