---
title: "CPU Scaling: scaling_max_freq unchangeable"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by amborle on 2006-11-27
Hey!

These are my available frequencies:

```
jens@maniac:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
1833000 1333000 1000000 
```

But for some reason scaling_max_freq is not set to max

```
jens@maniac:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
1333000
```

OK, so now i try to change it, but guess what happens:

```
jens@maniac:~$ sudo -i
Password:
root@maniac:~# echo 1833000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
root@maniac:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
1333000
```

It appears to my that I cannot change scaling_max_freq.

Scaling works fine, but my cpu will never go beyond 1.33GHz.

I am running a HP nc6320 with an Intel Core Duo 1.83GHz.

What can I do? No fun running my computer at 72% of capacity. :( 

Best regards, 
Jens

---

### Post by que on 2006-11-27
Have not tried to find a solution to this problem, but if you are booting from battery power try booting from AC.  I've noticed this problem with my HP dv5000 and as long as it is booted from AC power it can be unplugged and replugged with max scaling unaffected.

---

### Post by amborle on 2006-11-27
Sorry, I am booting from AC Power.

---

### Post by amborle on 2006-11-28
Issue fixed.

I updated to the lastest BIOS (F.09) from hp.com, of course I had to do it in Win ;)

Then i installed cpufrequtils (available through synaptics) and issued the following commands:

```
/usr/bin/cpufreq-set -c 0 -d 1.83GHz -u 1.83GHz -g ondemand
/usr/bin/cpufreq-set -c 1 -d 1.83GHz -u 1.83GHz -g ondemand

/usr/bin/cpufreq-set -c 0 -d 1GHz -u 1.83GHz -g ondemand
/usr/bin/cpufreq-set -c 1 -d 1GHz -u 1.83GHz -g ondemand
```

This solved my issues!

---

### Post by amborle on 2006-11-28
But after reboot my problems are back...

---

### Post by amborle on 2006-11-28
Ok, now I have rebooted/halted several times and now it seems to work!

To fix the scaling-problem on a nc6320 (probably true on other HP laptops too):

Update to latest BIOS from hp.com (for med F.09)

Add the following to /etc/init.d/halt and /etc/init.d/reboot

```
modprobe -r psmouse
```

Add the following to /etc/rc.local (of course edit to your max and min processor speeds):

```

/usr/bin/cpufreq-set -c 0 -d 1.83GHz -u 1.83GHz -g ondemand
/usr/bin/cpufreq-set -c 1 -d 1.83GHz -u 1.83GHz -g ondemand

/usr/bin/cpufreq-set -c 0 -d 1GHz -u 1.83GHz -g ondemand
/usr/bin/cpufreq-set -c 1 -d 1GHz -u 1.83GHz -g ondemand

```

After a reboot it should work.

For further reading, check out:

[http://home.no/slazz/nx6310/nx6310.html](http://home.no/slazz/nx6310/nx6310.html) (didnt you learn any german in school? =) )

[http://www.wolframschenck.de/nx6325.htm](http://www.wolframschenck.de/nx6325.htm)

---

