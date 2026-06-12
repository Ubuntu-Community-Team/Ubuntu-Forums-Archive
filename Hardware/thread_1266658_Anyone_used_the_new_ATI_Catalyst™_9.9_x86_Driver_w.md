---
title: "Anyone used the new ATI Catalyst™ 9.9 x86 Driver with the 3850?"
date: 2009-09-14
forum: Hardware
---

### Post by cocamoxb on 2009-09-14
Update: I jumped into the ATI<->Ubuntu relationship and it works well so far. My machine is really an Urban Terror box. I upgraded from the Nvidia Geforce FX 5200 to the ATI Radeon 3850 AGP. The steps I followed were:

[user@computer]$sudo apt-get remove nvidia*
--snip--
[user@computer]$reboot
[user@computer]$~/ati-driver-installer-9-9-x86.x86_64.run
--majik--
[user@computer]$SUCCESS!


This allowed me to go from running Urban Terror (Quake3 engine) in 800x600 with minimal settings, to 1600x1200 with full settings and still get full FPS. It was a well worth the $$ and 15 minutes.
**************************

I was considering an upgrade for my good ole' AMD Athelon 3200+ machine from the blasting GeForce FX5200 to the new fresh ATI HD 3850 super awesome card. Anyone got the new 9.9 driver, released 9/9/2009, to work with the 3850? Hope all is well, thank you in advance.


From the release notes:


Support for New Linux Operating Systems
    This release of ATI CatalystTM Linux introduces support for the following new operating
    system:
        RHEL 4.8 production support
        Ubuntu 9.04 production support

---

### Post by kleuck on 2009-09-15
Hello I am currrently using the 9.8 with a 3870, works fine with Debian 32 bits, but was pretty slow under Ubuntu 64 bits, don't know if the issue was in Ubuntu or the 64 bits kernel. I'll install the 9.9 right now.

---

### Post by kleuck on 2009-09-15
The 9.9 is perfectly working (Compiz, Sauerbraten)

---

### Post by cocamoxb on 2009-09-22
Update in first post. Works well.:guitar:

---

### Post by gurpal2000 on 2009-09-26
What kernel have you got and what Xorg version are you running?
I thought Jaunty comes with xorg 1.6 standard and the catalyst 9.9 docs say it won't work with anything less than xorg 6.8 ?

thanks

---

