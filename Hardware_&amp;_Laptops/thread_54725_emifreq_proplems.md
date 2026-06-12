---
title: "emifreq proplems"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by raghav_p on 2005-08-05
I have a centrino processor and have powernowd  scaling it.

To monitor temperature of my processor and for changing frequency, I installed emifreq. It worked UNTIL I rebooted the computer.

Now it displays temperature correctly but when I want to change frequency of my CPU, it gives me the following error. 

> Can't change the CPU speed.

The daemon in charge of changing the CPU speed is not started. Please do so if you want to control your CPU speed, and then click on the applet. 

I thought it might be that emifreq is started before powernow so to test I changed session priority to 0 and rebooted, but still no help. 

Any ideas?

---

### Post by s_p_a_r_k_y on 2005-08-06
yea, emifreqd needs to be started explicetly when you boot up. You can put a symlink in your /etc/rc2.d/ to /etc/init.d/emifreq-applet

do so by 
```
ln -s /etc/init.d/emifreq-applet /etc/rc2.d/S30emifreq
```
this will cause it to startup when you boot your computer...of course it will only work if you didn't change your initlevel. Check /etc/inittab for your initlevel. Its this line
id:2:initdefault:

Cheers

---

