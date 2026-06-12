---
title: "Weird problem wih my cd/dvd drive"
date: 2011-10-23
forum: Hardware
---

### Post by alpinito1 on 2011-10-23
Hello everyone,

I have a very weird problem. 

When I put any music cd that has been bought, I dont have any problem, I can read the cd. 

However the result of sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: TOSHIBA MK8025GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: KA02
       serial: 56GJ1585S
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009ab3c

It seems the cd/dvd drive is not recognied at all. 

If I put a burned cd, some times i can read it but some times not. 

Finally when I put a blank cd,  it is not detected at all.

I have ubuntu 11.04.

Thank you guys for your help

---

