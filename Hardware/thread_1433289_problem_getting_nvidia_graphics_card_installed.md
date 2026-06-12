---
title: "problem getting nvidia graphics card installed"
date: 2010-03-18
forum: Hardware
---

### Post by ptmcl on 2010-03-18
I am running Ubuntu 9.10 on VMware workstation 7.00, my graphics card is Nvidia Geforce 8400M GS. I think the issue is that for some reason the graphics card is being detected by Ubuntu. I had this problem with a fresh installation of Ubuntu 9.10 but now its been a couple weeks, I did get my card working with Ubuntu 7.something though. 

lspci | grep -i nvidia 
prints out nothing

locate xorg.conf
Says I don't have the file, I manually checked etc/X11/xorg.conf and its not there. So I think this is probably the cause of my problem.

Any suggestions what I should do? I consider myself a beginner to linux but I can get around. Any help would be great, thanks!

---

### Post by N92 on 2010-03-18
Have you tried going to your toolbar System - Administration - Hardware Drivers
And activating the driver from there

---

### Post by ptmcl on 2010-03-18
yes, no drivers are listed

---

### Post by jocko on 2010-03-18
> **ptmcl said:**
> I am running Ubuntu 9.10 on VMware workstation 7.00, my graphics card is Nvidia Geforce 8400M GS
In a virtual machine, the guest OS only see a virtual graphics card, not the real one, so installing nvidia drivers will only screw things up for you.

---

