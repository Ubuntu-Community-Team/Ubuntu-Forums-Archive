---
title: "Control Cpu and wireless"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by adolfotregosa on 2006-06-08
How do i control my cpu speed for longer battery (centrino) on xubuntu ? And how do i search for wireless networks ??

---

### Post by jolinux on 2006-06-09
[QUOTE=adolfotregosa]How do i control my cpu speed[/QUOTE]

I am interested also

---

### Post by compmodder26 on 2006-06-09
Here is what I did to automate the job of frequency scaling for my Thinkpad T60.  Some people might say "why do this when you can install a daemon like powernowd to do it for you?"  Well the answer is that powernowd didn't work like I wanted it to.  It always left my cpu at the lowest frequency level even when I was on ac power.  So I created a few scripts that would fix that:

**Do all these steps as root.**

In the directory /etc/acpi/, there are two subdirectories named battery.d and ac.d. You can place scripts in here that will be executed whenever you switch power sources. Let's start with battery.d:

Create a file called "cpus_scaling.sh" and place the following lines in it:

```
#!/bin/sh 
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

if you have multiple processors/cores/etc. duplicate the last line for each cpu that ubuntu recognizes and change cpu0 to cpu1, cpu2, etc.



Now for ac.d:

Create a file called "cpus_scaling.sh" and place the following lines in it:

```
#!/bin/sh 
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
```

Again if you have multiple cpus/cores/etc. duplicate the last line for those recognized cpus



Change the permissions on all the files you created to allow execution.


These work great when the laptop is already on, but when you first turn it on, ubuntu doesn't execute the scripts in battery.d or ac.d. So I had to create a initialization script to run on startup.

Create a file in /etc/init.d/ called "getpower" and place the following code in it:

```
#!/bin/bash 

POWERSTATE=`grep -c off-line /proc/acpi/ac_adapter/AC/state` 

if [ $POWERSTATE != 0 ]; then 
    /etc/acpi/battery.d/cpus_scaling.sh 
else 
    /etc/acpi/ac.d/cpus_scaling.sh 
fi
```


change the permissions to allow the file to be executed.

Finally, in all the rc.d folders in /etc (rc2.d, rc3.d, rc4.d, rc5.d) except for rc1.d and rc6.d place a symbolic link the "getpower" script in /etc/init.d:


```
ln -s /etc/rc2.d/S99getpower /etc/init.d/getpower
```


do this for all the rc folders I listed above.



As for wireless, install network-manager and you should be able browser available wireless networks.

---

### Post by mority on 2006-06-18
Thanks for those instructions but they did not really work for me :(
My T30 was constantly running with low frequency (1200 MHz instead of the full 1800 MHz). After following your instructions it is now constantly running on 1800 MHz but does not scale down if it runs on battery. Well, but that's still better then always running with low frequency.

You made a little mistake here:
[QUOTE=compmodder26]
```
ln -s /etc/rc2.d/S99getpower /etc/init.d/getpower
```
[/QUOTE]
It should be ```
ln -s /etc/init.d/getpower /etc/rc2.d/S99getpower
``` I guess.

edit: corrected a typo.

---

### Post by Egalus on 2006-06-19
Another way to get cpuclock control is to use powernowd.

---

### Post by compmodder26 on 2006-06-19
[QUOTE=mority]Thanks for those instructions but they did not really work for me :(
My T30 was constantly running with low frequency (1200 MHz instead of the full 1800 MHz). After following your instructions it is now constantly running on 1800 MHz but does not scale down if it runs on battery. Well, but that's still better then always running with low frequency.
[/QUOTE]

Try this:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

This will list the available scaling governors for your system.  Make sure that "performance" and "ondemand" are present.

If so, try this:

With the laptop running on ac power do:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

You should see "perfomance"

Do the same thing with the laptop running on battery power and you should see "ondemand".

If this is the case, the scripts are doing what they are supposed to do but your laptop isn't handling the ondemand governor well.  For more information on governors look at the section on "Using Frequency Scaling Governors" on this [page]("http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling")

---

### Post by mority on 2006-06-20
[QUOTE=compmodder26]Try this:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

This will list the available scaling governors for your system.  Make sure that "performance" and "ondemand" are present.

If so, try this:

With the laptop running on ac power do:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

You should see "perfomance"

Do the same thing with the laptop running on battery power and you should see "ondemand".
[/QUOTE]


The scripts do not seem to work:
```

root@ash:~# cat /proc/acpi/ac_adapter/AC/state
state:                   on-line
root@ash:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
performance
root@ash:~# cat /proc/acpi/ac_adapter/AC/state
state:                   off-line
root@ash:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
performance

```

Do you maybe have any idea why? I am pretty sure that I followed your instructions correctly and in detail.

I noticed that I get an error if I try to start /etc/acpi/battery.d/cpus_scaling.sh manually. Look at the output below:
```

root@ash:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance
[color=red]root@ash:~# /etc/acpi/battery.d/cpus_scaling.sh
/etc/acpi/battery.d/cpus_scaling.sh: line 2: echo: write error: Invalid argument[/color]
root@ash:~# /etc/acpi/ac.d/cpus_scaling.sh
root@ash:~# cat /etc/acpi/battery.d/cpus_scaling.sh
#!/bin/sh
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

root@ash:~# cat /etc/acpi/ac.d/cpus_scaling.sh
#!/bin/sh
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor


```
In the first line you can see that the "ondemand" governer should be supported.
/etc/acpi/ac.d/cpus_scaling.sh runs without errors. I also posted the scripts itself so you can check that there are no errors in it.

---

### Post by compmodder26 on 2006-06-20
hmm... the contents of the files look correct.  I'm a little stumped.  All I can thin of is to check to make sure the permissions of the cpus_scaling.sh script in the battery.d directory is set to execute.

---

### Post by mority on 2006-06-20
Hooray! I replaced 'ondemand' with 'powersave' in /etc/acpi/battery.d/cpus_scaling.sh and now it works perfectly.

```

#!/bin/sh
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Thanks for all your help!

---

### Post by wiljohnson on 2006-06-20
[QUOTE=adolfotregosa]How do i control my cpu speed for longer battery (centrino) on xubuntu ? And how do i search for wireless networks ??[/QUOTE]
To scan for wireless networks download Wifi-radar

---

