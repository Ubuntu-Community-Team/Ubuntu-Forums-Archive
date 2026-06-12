---
title: "ubuntu 15.04 will not load with nvidia optimus"
date: 2015-08-06
forum: Hardware
---

### Post by jbb1996 on 2015-08-06
hi i installed ubuntu 15.04 5 days ago and it worked then today's ago I installed some updates and now ubunut will not load with the nvidia card??

my computer is a lenovo t420 

this is the output when I try to switch form the intel to the nvidia card with sudo prime-select nvidia

> 
Info: the current alternatives in use are: ['nvidia-352-prime', 'nvidia-352-prime']Info: selecting nvidia-352 for the nvidia profile
update-alternatives: using /usr/lib/nvidia-352/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode
update-alternatives: using /usr/lib/nvidia-352/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode




I have tried reinstalling ubuntu and the something happened

---

### Post by efflandt on 2015-08-07
Not sure how that works in 15.04, but in 14.04 on my laptop, when using NVIDIA X Server Settings to switch from Nvidia to Intel, all I have to do is log out of X and log back in. But when I switch from Intel to Nvidia I have to reboot for that to take effect. So if you are expecting that to switch to nvidia on the fly, not sure if that works at this time.

---

