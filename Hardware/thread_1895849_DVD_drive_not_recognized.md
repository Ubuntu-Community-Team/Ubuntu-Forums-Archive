---
title: "DVD drive not recognized"
date: 2011-12-15
forum: Hardware
---

### Post by alpinito1 on 2011-12-15
Hello every one,

I'm having a problem with my dvd drive. Ubuntu seems to not find the cd/dvd rom. 

the result of 
sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
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
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

which means that the cd/dvd drive is not found.

However, if i reboot the computer by keeping for example a blank dvd inside the drive, when ubuntu boots it does recognize the cd/dvd drive and I'm able to burn the dvd/cd.

So the question is somebody else has come across a similar problem, or if someone has any idea.

Thank you.

Best,

Daniel

---

