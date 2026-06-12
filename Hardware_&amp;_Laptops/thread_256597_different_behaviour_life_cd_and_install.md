---
title: "different behaviour life cd and install"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by jvhove on 2006-09-13
Folks,

I was looking for a suitable linux distribution on my Toshiba Tecra 9100. Great, the install cd is also a life cd, which allowed me to test the system. And it worked great, wireless, sound, video, .... :D 
So, I formatted my redhat :evil:  partition and replaced it with ubuntu.
After booting the system my wireless no longer works :( 

What is the difference between the lifecd system and the installed one ? This might help me in my search for a resolution.

---

### Post by jvhove on 2006-09-13
Found it

related with other errors I found on the forums.
strange that lifecd works and actual install doesn't, but ok,
if you run into issues with your wireless on a toshiba tecra 9100 or orinoco chipsets, hereunder the solution :

add the following lines to /etc/modprobe.d/blacklist
blacklist hostap
blacklist hostap_cs

---

