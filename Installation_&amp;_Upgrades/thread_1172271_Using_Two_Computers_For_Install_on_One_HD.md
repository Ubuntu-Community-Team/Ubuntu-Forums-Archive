---
title: "Using Two Computers For Install on One HD"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by Rory Williams on 2009-05-28
Hello All, 
I recently did an install of xubuntu 9.04 on an older laptop. 
It had no CD drive, couldn't boot from usb, and has some pretty low specs. I installed it onto the first computer's hard drive from another, much newer, system with functioning CD and all that good stuff. The OS is now running "fine" on the old system, except that it is pretty slow. What may have happened is that it built itself for the newer system, and didn't change when I plugged it into the older one. 

So, basically, my question is: Is there any way to modify the OS so that it recognizes the correct hardware? 

Thanks

---

### Post by lemming465 on 2009-05-30
The first thing I'd try is ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` followed by a reboot.

How much memory does the older system have, and how much slower is the CPU and/or graphics chip?

---

### Post by Rory Williams on 2009-05-31
I put the code into terminal and it started "depmod" and then shut off.

I turned it back on and it seemed to be a little faster. 

The original install was on a 3GHz Pentium 4 with 1.5 Gigs of RAM.
Transferred it to a 500Mhz Pentium 3 with 192 MBs of Ram.           

Thanks for the help. :p

---

