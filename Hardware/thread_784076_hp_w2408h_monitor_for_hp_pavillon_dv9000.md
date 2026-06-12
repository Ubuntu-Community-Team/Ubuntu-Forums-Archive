---
title: "hp w2408h monitor for hp pavillon dv9000"
date: 2008-05-06
forum: Hardware
---

### Post by Jabz.biz on 2008-05-06
Hi, 
I just bought the hp w2408h (24") monitor for my hp pavillon dv9000. Unfortunately Hardy does not detect the monitor. I tried System > Preferences > Screen Resloution > Detect Displays, it did not work, nothing happens. 

The screen itself is fine, cables are working...I checked with my Windows laptop. :( OK, now I need a lil` help from you guys, what can a noob do to get it working? Btw. I`m on NVIDIA.

Thank you for your help. 
Regards, Jab

---

### Post by Jabz.biz on 2008-05-06
OK, a friend helped me solving the problem. 
I just had to install a Nvidia manager.

Add/Remove Applications > Nvidia X server Settings 

You can than find it under the Administration Tag and work yourself through the setup. In my case that was "X Server display configuration". 

:KS

---

### Post by EduardoMartins on 2009-06-14
Running Ubuntu 9.04, I am trying to get a proper resolution for a HP w2408h on a Lenovo 3000 N100 with:

Intel Graphics Media Accelerator 950 chipset (up to 128MB)
                       64MB nVidia GeForce Go 7300
                       128MB nVidia GeForce Go 7300

If I got it right, I am supposed to:

1) Install Nvidia X Server and some nvidia-glx-??? driver
2) run "sudo nvidia-xconfig"
3) edit the "Monitor"entry for the nvidia-xconfig file.

What exactly am I supposed to write/change there?

Thanks,

Eduardo

---

### Post by Jabz.biz on 2009-06-16
Hey, 

you are lucky, I'm still using this laptop! Although I have fedora running on it right now, I have tested Ubuntu 9.04 on it as well (really installed it).

The x conf-files are totally empty and I had a perfect screen resolution out of the box. Even the external monitor was discovered and had a proper resolution. As far as I can tell...everything should be cool. 

Go to Preferences > Display and see if you can work it out there. 
Good Luck!

---

