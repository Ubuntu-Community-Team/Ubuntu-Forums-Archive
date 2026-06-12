---
title: "insmod on boot"
date: 2009-09-29
forum: Hardware
---

### Post by jdt141 on 2009-09-29
Hey all -

I'm having the hardest time getting a driver to load on boot. Here's the deal.

PC/104 stack running ubu8.04. I've got a Devicenet card which, when i issue the following command:

```
sudo insmod applicomio.ko irq=6
```

All is well! The device ```
/dev/ac
``` is created, the driver appears on lsmod, and the card shows up when i cat /proc/interrupts. 

I've tried to get this to work on boot by placing an "applicomio" line in my /etc/modules file, added a file, applicomio, to the /etc/modprobe.d/ directory with the following contents:

options applicomio irq=6

and placed the applicomio.ko file in /lib/modules/'uname -r' directory per modprobe 8, yet, when i reboot, I get no love. I'm *sure* its something I'm overlooking. Any help would be greatly appreciated. Thanks!!

---

### Post by jdt141 on 2009-09-30
bump

---

### Post by i.r.id10t on 2009-09-30
At what point during the boot process do you need it?  You could add a small script to do it in /etc/init.d and call it from /etc/rc2.d  so it loads before whatever uses it loads, or if you just want it "up" when you can log in you could add it to /etc/rc.local

---

### Post by Ayuthia on 2009-09-30
Have you run
```
sudo depmod -a
```It will rebuild the module dependency list and your system should be able to find the module in /lib/modules afterward.

---

