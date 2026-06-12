---
title: "After kernel update, reduced battery life"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by ilLorenz on 2008-02-05
Hi everybody, 
Hope that you can help me with this little issue
I have a Dell Inspiron 1501 with an AMD Turion  64 x2, 1,9 GHz. I just update the kernel via the Synaptics Update manager (at least, I suppose it was the kernel, has become available only in the last two days). After I did so, my estimate battery life has been reduced of about 30/40 minutes, and I gat during boot an error message like this:

/etc/rd.2/S20powernowd: 156 : cannot create /sys/devices/cpu/cpu0/ /cpufreq/scaling_governor : Directory nonexistent    Cpu frequency scaling not supported
[RIGHT][OK][/RIGHT]

I never got this error before, so I suppose it has something to do with the update I made...

Please help me, I haven't got a clue on how to make this thing work thank you

---

### Post by Yellow Pasque on 2008-02-05
Sigh, why does it seem like the updates from Ubuntu break things as of late? They're really dropping the ball lately. Anyway...

It looks like the /etc/rc2.d/S20powernowd script is looking in /sys/devices/cpu when it should be looking in /sys/devices/system/cpu.

I'm not sure how to fix that at the moment.

---

### Post by Bronto on 2008-02-05
Must be something else.
I have the same laptop model and nothing happened after kernel update.

---

### Post by ilLorenz on 2008-02-06
Hi, I got a look within the S20powernowd script and there is not a place where I can replace the directory... If anybody has an advice, please post; I'm thinking about reinstall, but maybe it would be a bad idea...

Thanks

---

### Post by grdnwsl on 2008-02-06
Just want to let you know you're not alone.  I am experiencing the same problem after the latest kernel update this week.  I'm running on a Fujitsu Siemens LifeBook P7010 with an Intel Pentium M 1.2GHz.  Frequency scaling was working fine before the kernel update.

---

### Post by Yellow Pasque on 2008-02-06
Here you go. It looks like there's a patch on this page:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132271](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/132271)

---

### Post by ilLorenz on 2008-02-09
OK, seems like I found a likeable explication for that problem: the Ubuntu Gutsy (32bit) installation on a Dell Inspiron 1501 suffers of the infamous MP-BIOS BUG #81 timer not connected to IO-APIC, wich influences the energy mangement and, because of that, frequency scaling. Apparently the new kernel cannot overcome the problem like the past one di.
I would like to notice that in Windows  got more than 3 hours of battery life, half an hour more than in Ubuntu. 
So the problem is, imho, related to the BIOS energy settings that the kernel cannot overcome.
If you have the same one or a similar one wich has a Phoenix BIOS and you succeded in fixing the BIOS bug, please let me know! I would expecially like to know if the proplem represents also with a 64 bit installation, and your bios version could also be important (mine is 2.7).

Thank you all in advance

---

