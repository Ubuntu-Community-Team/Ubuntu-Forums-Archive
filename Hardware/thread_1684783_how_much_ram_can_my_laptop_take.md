---
title: "how much ram can my laptop take"
date: 2011-02-09
forum: Hardware
---

### Post by fat-pat on 2011-02-09
is there a way to find out the max ram the motherboard in my laptop can take??

i know of programs that can do this in windows is there a ubuntu version

could i run the windows program in wine??

---

### Post by cipherboy_loc on 2011-02-09
Most of the laptops can take about 4GB of RAM. Do most people need this much? No. I rarely use over 1/3 my current RAM (2GB). My laptop has 2 bays for RAM, so in theory you could get 2 x 4GB RAM cards and run at 8GB, but you would need a 64-bit processor and OS. Post the output of:

```

lspci

```
and
```

cat /proc/cpuinfo

```
and
```

free -m

```

And somebody might be able to tell you how much RAM your system can take. They might need the make/model number of the system.



Cipherboy

---

### Post by PRC09 on 2011-02-09
Check the manufacturer website.The amount of ram will vary from machine to machine, not only the amount but speed,type, and how much the chipset and bios will recognize...

---

