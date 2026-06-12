---
title: "Undervolting Atom N450 with PHC"
date: 2010-03-10
forum: Hardware
---

### Post by dJ85 on 2010-03-10
Hey folks,

I've got problems to get the phc-intel module to work.
Compiling the sources (phc-intel-0.3.2-10) against kernel 2.6.31-20-generic-phc went without problems, also inserting the module goes without any error message.

System:
- Asus Eee PC 1005p with atom N450
- Karmic

```

dennis@dennis-laptop:~$ lsmod |grep phc
phc_intel              11912  0 

``````
dennis@dennis-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls 
10:30 8:20 6:19 
```Until here everything seems to be fine. But altering the vid's i.e. by 

```
root@dennis-laptop:~# echo "30 20 15 " > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids
```does not have any effect. I verified this by setting all values to 0 on both CPU's. That didn't freeze the system, so I think my conclusion is correct. ;)

What could be going wrong here? Is phc maybe just not capable of changing the voltage for this cpu?


I'd appreciate any ideas.

Thx,

dJ85

---

### Post by kamatschka on 2010-04-27
I have the same issue . 

phc configurations doesent take any effect on my Intel Core 2 Duo T7300 (2GHz) ..

I've installed the kernel and the patch on Ubuntu 10.04

I would be really glad if someone can help.

---

### Post by gabryp on 2010-06-13
the same problem on Samsung N220 with Atom N450

---

