---
title: "Ubuntu not detecting second hard drive but BIOS shows two hard drives"
date: 2020-03-03
forum: Hardware
---

### Post by ravi-s on 2020-03-03
I wanted to dual boot my PC with two hard drives, one containing Windows and the other Ubuntu. Now my Ubuntu does not detect the second hard drive, i tried *sudo fdisk -l* and it only shows */dev/sda* which is my linux drive. i know my other hard disk is working because i'm able to log into windows when i boot into that using BIOS.

---

### Post by Autodave on 2020-03-03
Did you disable *fast boot* in Windows?  If not, then Ubuntu will not see it.

---

### Post by CelticWarrior on 2020-03-03
> **Autodave said:**
> Did you disable *fast boot* in Windows?  If not, then Ubuntu will not see it.

It's Fast Startup and it causes a lot of trouble but the physical drives should be visible anyway. 

The problem here, I suspect, is either RAID or Intel RST SATA modes, It needs to be changed to AHCI but that implies installing AHCI support in Windows first or it won't boot after the change.

---

