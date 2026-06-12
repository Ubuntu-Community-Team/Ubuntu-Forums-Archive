---
title: "showing less ram in O.S than in BIOS"
date: 2015-08-22
forum: Hardware
---

### Post by avishek_arora on 2015-08-22
hi everybody , 

my BIOS showing 6gb of ram as i have in my desktop. so after installing UBUNTU 15.04 in my desktop now inside UBUNTU'S about this computer -  it's showing only 2.9 gb of ram. i don't know why it is happening as i'm new to ubuntu. please solve this problem as the ram dealer says that ram is working fine.

---

### Post by dino99 on 2015-08-22
you might have missed to enable a bios setting to 'extend' the ram over the first 4 Gb; otherwise that should mean you have a lot of shared memory (for example a graphic card without memory; so using the mobo ram for its needs)

---

### Post by avishek_arora on 2015-08-22
how to fix this ?

---

### Post by Yellow Pasque on 2015-08-22
Look for "memory remapping" or "memory hoisting" settings in your BIOS.
Also, confirm that you installed a 64-bit (x86-64) version of Ubuntu:
```
uname -a
```

---

### Post by Bucky Ball on 2015-08-22
> **Temüjin said:**
> 
Also, confirm that you installed a 64-bit (x86-64) version of Ubuntu:
```
uname -a
```

^^^
This. 32bit OS won't see all that RAM.

---

### Post by avishek_arora on 2015-08-23
ok i'll look for the bios setting and update you. 
i did run the uname -a command  it gives : 

```
 avishek@avishek-desktop:~$ uname -a
Linux avishek-desktop 3.19.0-27-generic #29-Ubuntu SMP Fri Aug 14 21:43:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
so it is confirmed now that i have installed a 64 bit version of ubuntu.

---

### Post by avishek_arora on 2015-08-23
well Temujin after enabling the memory remapping from bios the problem is solved. now it showing the 5.8 gb of memory. thank you everyone for your support.

---

