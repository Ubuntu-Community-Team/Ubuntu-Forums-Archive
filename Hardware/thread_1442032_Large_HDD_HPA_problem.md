---
title: "Large HDD HPA problem"
date: 2010-03-29
forum: Hardware
---

### Post by MightyMouse on 2010-03-29
Hi,

I have recently exchanged my broken 80Gb HDD on my Cybermaxx Laptop with a 320Gb HDD.
I have flashed my BIOS to the most recent version I could find (and my Laptop is not very new but it came with Windows XP so it actually should support larger disk drives).
During installation of either Windows or Ubuntu I only get to set up 137Gb, the rest of the drive is not available. I have also checked with gparted if there is unused space but found nothing. Starting with the Live CD and checking with the Disk utility results in the same. And obviously in my BIOS I only see 137Gb and have also no options to activate any LBA or other support for large drives. But as has been frequently pointed out on numerous message sites, Linux is not supposed to determine the HDD size based on the BIOS information.

I have done an extensive search on the Net and have already partitioned my drive with a 500 Mb /boot partition at the beginning of the drive as has been repeatedly suggested (+ swap and seperate / and /home partitions). Yet this hasn't helped.

I have found some messages about the HPA being a problem and when I do 

grep -i hpa /var/log/dmesg

I do get in fact the confirmation that 

[    1.697020] ata1.00: device aborted resize (268435456 -> 625142448), skipping HPA handling

I have tried the following: I have added

libata.ignore_hpa=1

to /etc/default/grub and then done update-grub, but that hasn't helped. I am not sure if this is the correct way to approach this problem anyhow since the grub loader is now grub2 and this might not work at all.

I was wondering if someone has a solution for this HPA handling issue or at least some pointers to where or how to get the rest of my drive to work?

All help is welcome,

MightyMouse

---

### Post by MightyMouse on 2010-03-30
Anybody with an Idea about how to disable HPA??????????

---

