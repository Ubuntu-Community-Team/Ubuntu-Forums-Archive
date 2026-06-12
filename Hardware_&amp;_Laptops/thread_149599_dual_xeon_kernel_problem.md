---
title: "dual xeon kernel problem"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by mox on 2006-03-24
Hi,
I can't solve this problem:

info
motherboard intel with 2 xeon at 2 ghz (32bit)
adaptec 2100S ultra 160 scsi3 raid 1 with 2 +2 HD in raid1 
...

the only kernel accepted is a 2.6.x-386; if I try to install a 686 or smp-686 kernel the system always go in kernel panic; I try to set no-acpi, but the result is the same.

The situation is that I have a multiprocessor server with a single processor 386 cpu, and the general speed is very poor

There are anyone can help me?

thank
mox

(sorry for my very bad english)

---

### Post by benshort on 2006-08-21
Hi, 

Im having the same problem with dapper. I install the system using raid1. When i upgrade to the 686 smp kernel the system wont boot. I think that the 686 smp kernel dosent have the raid support built into it where as the 386 does. I dont know why.

Ben

---

### Post by tribaal on 2006-08-21
I installed a server version on the exact same setup without a twitch... Did you check your install CD's integrity? Perhaps start with a server install then install ubuntu-desktop if you want a GUI...

Just my 2c...

- trib'

---

### Post by Centx on 2006-11-06
Ive got this problem too, I have a dual Xeon setup with nvidia Graphics card. When i try tried to install SMP-kernels from apt, the machine locked when i was to log in, and doing a vanilla kernel setup didnt see my HDD's
when i tried the Edgy Eft live cd, which i belive have SMP by default, the machine would lock on start up, or rather it wouldnt accept any input from neither my mouse or keyboard. I tried the 686-SMP, amd64 and k7 kernels (just in case)

it would be really nice if someone had some help on this :-k

It worked with Fedora Core 5... and then my HDD's was recognised in the right order too

---

