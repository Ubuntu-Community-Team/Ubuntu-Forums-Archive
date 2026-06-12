---
title: "procesor state applet"
date: 2008-05-19
forum: Hardware
---

### Post by gresha on 2008-05-19
Hello,

I have some problem with mine cpu freq control i cant control it on my own, cant change anything its all the time set at -performace

```

gresha@gresha-laptop:~$ sudo cpufreq-set -g ondemand -d 798000 -u 1862000 -c 1
[sudo] password for gresha: 
gresha@gresha-laptop:~$ sudo cpufreq-set -g ondemand -d 798000 -u 1862000 -c 0
gresha@gresha-laptop:~$

```

when i write it into terminal i can change settings in applet but at short time (about 5minuts) i can set then all functions, but it automaticly set to performance again, then i cant do nothing.

Laptop: Asus F5v
cpu: core 2 duo T3130

---

### Post by sdennie on 2008-05-19
What is the output of:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

And, also, what is the output of that command after you run:

```

sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

---

### Post by gresha on 2008-05-20
```

gresha@gresha-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
performance
gresha@gresha-laptop:~$ sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
[sudo] password for gresha: 
gresha@gresha-laptop:~$ 



```

---

### Post by sdennie on 2008-05-20
Ok.  But, what is the output of:

```

sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

And, does it make a difference in the frequency scaling?

---

### Post by gresha on 2008-05-20
yup it helped ;] thx

EDIT:

it seem working but now it crash, i cant change it :/ 
```
gresha@gresha-laptop:~$ sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
gresha@gresha-laptop:~$ 
``` -thats what i get from this command


```
gresha@gresha-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
gresha@gresha-laptop:~$ 
```- and the 2nd command

---

### Post by gresha on 2008-05-20
*bump*

---

