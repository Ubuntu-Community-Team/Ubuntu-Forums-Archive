---
title: "APIC kernel panic only when overclocking"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by Turboaaa2001 on 2007-07-18
My PSU is a 400w Antec
My MOBO is an EPoX with VIA chipset (I don't remember the actual model but the BIOS is updated)
Sempron 3300+ @ 2200MHZ stock (I want to run 2530MHZ)
728MB PC-2100
Samsung 40GB HD
Seagate 300GB HD
Maxtor 300GB HD
Generic CD-ROM
Rage 128 PCI video

Right now I'm running 6.06LTS.


------------------------------------------------------------------

Here's my issue, the above system is running as my fileserver. I also have it running BOINC so I would like to have my CPU clocked up to produce more results. The problem is that I ran into an issue where I needed to re-install the OS and at the time the CPU was running at 2530MHZ. When I tried to re-install I kept getting the kernel panic with the APIC error.

I found out that I could install at the stock frequency of 2200MHZ. I'm running at this speed now but would like to go beyond. I've posted for help on getting the install to work and I have looked at the forum records for an answer to this problem.

My question is can I increase the clock speed now that the system is running fine? I want to make sure because I'm still getting use to how Ubuntu reacts and I don't want to go through the hassle of fixing it again.

---

### Post by davidsrsb on 2007-07-18
If the install fails with overclocking, your PC is not stable at the higher speed. I would run the memory test from the install cd to check that the machine is stable at the "official" clock speed.

File servers don't need high performance cpus as they are not doing gui work. I have old PIIs running OK,
RAM size and disk I/O is far more important.

---

### Post by Turboaaa2001 on 2007-07-19
Heres the thing. I already tested the memory (had some replaced a while back) and I know it's stable at the increased speeds due to running it at that speed for over a year.

It runs fine with Windows and runs stable otherwise. This problem started when my installation became corrupted after a power failure and I started the new install.

FYI, I'm aware that a fileserver does not need the speed. If that was the only use for the rig I would down-clock to conserve energy. I also use the rig to crunch numbers 24/7 because of the low overhead of a fileserver.

I just need to know if someone else has had been able to increase the speeds after installing Linux.

---

