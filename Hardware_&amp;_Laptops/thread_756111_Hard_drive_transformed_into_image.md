---
title: "Hard drive transformed into image"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by nico243 on 2008-04-15
Hi everyone, I have a laptop with Vista and Kubuntu. I installed updates from Microsoft and my vista cannot boot anymore, so I made a copy of all my C: drive using de command

sudo dd_rescue /dev/sda2 /dev/sdb1

sda2 being my C: and sdb1 being my 250Gb portable hard drive

Normally, this command must be used putting at the end of the last drive name, 

/backup.img

but it couldn't work for me, so I didn't used it.

The problem is, the dd_rescue made my hard drive a whole boot disk of my C:, named OS_Install. I copied everything I need and that's great, but now, I want to remove this formmating of "boot img" of my hard drive.

A few things useful to know is that now, my HD size is 34.5 Gb, which is the size of my C: partition, and cannot see anything I had on it before (LOTS of .iso...) 

So, if someone knows how to change back my HD, please, let me know. 

Thanks for your future help.

---

