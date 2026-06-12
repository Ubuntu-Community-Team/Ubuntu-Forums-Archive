---
title: "change powerstate of ati card through script"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by santo on 2006-10-24
I want to switch between powerstates when I switch to/from battery power.

To do this, I wanted to add the necessary aticonfig calls to a script in ac.d and battery.d, like this:

/etc/ac.d/80-ac.sh:
```

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
#aticonfig --set-powerstate=3
#aticonfig --set-powerstate=3 --effective-now
DISPLAY=:0 aticonfig --set-powerstate=3

```

/etc/acpi/battery.d/20-battery.sh
```

#!/bin/sh
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
#aticonfig --set-powerstate=1
#aticonfig --set-powerstate=1 --effective-now
DISPLAY=:0 aticonfig --set-powerstate=1

```


But I get following error in /var/log/acpid:
```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Unable to open display `:0'.

```

or (when I don't specify DISPLAY=:0):
```

Error: Unable to open display `'.

```

I think the problem is that the scripts are called with root privileges,
because when I call the script from the command line as a regular user, everything works fine
and as root I get the same errors

But I don't know how I can let them execute as the regular user.

Using sudo doesn't seem to solve the problem either:
```

root:~# sudo -u testuser aticonfig --set-powerstate=1
Error: Unable to open display `'.

```

---

### Post by santo on 2006-10-24
Found the solution in the Gentoo forums:

```

xhost +local:

```

> 
so that local users (like root, or the one your acpi script is run as) other than the one logged in can access the x display


---

