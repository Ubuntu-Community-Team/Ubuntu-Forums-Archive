---
title: "Headphone Jack on Acer Extensa 5620 not working with Ubuntu 7.10"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by paulchuck on 2008-01-18
Hi All,

There is some info on this issue in other posts but I didn't find anything for exactly this issue or a solution that worked for me.  I have an Acer Extensa 5620 with Ubuntu 7.10 installed.  Most things work but today I figured out my headphone jack doesn't work.  What I have tried so far is to install linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386 and added the line options snd-hda-intel model=acer to the top of the file /etc/modprobe.d/alsa-base and then rebooted.  Any help would be much appreciated.  Let me know if there is any more info you need.

Here is some info on the issue:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)  see Method E

THanks,


Paul :confused:

---

### Post by paulchuck on 2008-01-18
Realized I forgot to describe the problem.  When I plug in headphones sound continues to play through the external speakers.

---

### Post by Tribuntu on 2008-05-29
Ive been having the same problem. I thought it was an internal error with the hardware but if your having the same problem I think its an Ubuntu error. :( Hopefully someone knows how to fix this.

---

