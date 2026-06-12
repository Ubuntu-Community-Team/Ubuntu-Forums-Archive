---
title: "3Ware 9500S RAID Array Detection"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by TheDelChop on 2009-03-02
Guys,

I am fairly new to Ubuntu, and am doing my best to install Intrepid Ibex onto my newly created RAID Array.  

I am using hardware RAID, a 3Ware 9500S 4 Port SATA RAID controller, which I have sucesfully setup using their BIOS manager.  

However, when I try to install Ubunutu using my Live CD, it doesn't find the RAID Array.  

Can anyone point me in the right direction?  I can only really find instructions on setting up fakeRAID, which obviously doesn't apply to me.  

3Ware states the the driver for this card is included in the Linux Kernel, but how do I know if its detected the RAID card?

THanks in advance, 

Joe

---

### Post by TheDelChop on 2009-03-03
So for anyone else who is having this problem I found a temp solution and thought I'd post it for all those who may come across this in the future.

The 3ware driver has a problem running on systems that have a 64-bit OS and more than 2GB of memory.  Don't ask me why, but as soon as I removed my 2x512MB RAM sticks, so that I only had 2 GB of RAM, Grub recognized my RAID array just fine, it installed and worked well.

I emailed 3ware support for a solution, and I have read allegedly that there is an upstream 3Ware Enginerring fix, and I will post here again if they get back to me.

---

