---
title: "weird startx error"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by Tigey on 2005-07-28
okay so ive installed everything and it went smooth. started up in the command prompt. not so bad right? tried to run startx. i got this error it was something like "found screens, but couldnt use" 

my specs:
pentium IV 2.8 ghz
Geforce 4 MX4000 PCI
762 megs of ram
eView 17f monitor (17 inches)

i just dont know what to do to get x to start. can anybody help me?

---

### Post by mad_scientist03 on 2005-07-28
Try a 'sudo dpkg-reconfigure xserver-xorg' , and you can go through the Xserver configuration routine again. If you still see the errors when you run 'startx', look at /var/log/Xorg.0.log or type 'dmesg', and post the errors you see.

---

