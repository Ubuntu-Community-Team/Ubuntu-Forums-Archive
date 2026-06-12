---
title: "CPU throttled back"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by spotslayer on 2006-11-25
Good evening all,  I have a Lenovo 3000 with dual 1.66ghz processing power. This sounds great. The issue is the power management is throttling them down to 1ghz, at least that is what the applet is showing. If that is correct and they are running a 1ghz I would should like to know how I can get them up to the 1.66ghz at which they are designed to operate. I have searched the forums and come up empty. I have searched my system for some type of configuration file and have come up empty there as well. Can someone help me out?

David

---

### Post by rbalfour on 2006-11-25
> **spotslayer said:**
> Good evening all,  I have a Lenovo 3000 with dual 1.66ghz processing power. This sounds great. The issue is the power management is throttling them down to 1ghz, at least that is what the applet is showing. If that is correct and they are running a 1ghz I would should like to know how I can get them up to the 1.66ghz at which they are designed to operate. I have searched the forums and come up empty. I have searched my system for some type of configuration file and have come up empty there as well. Can someone help me out?

David

at shell:

$ echo performance > /sys/devices/system/cpu/*/cpufreq/scaling_governor

then

$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

report back if your cpu are at there highest speed.

---

### Post by spotslayer on 2006-11-26
Results posted below. There is no change. Still running at a throttled speed.



david@DsLNVO:~$ echo performance > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$

Every 1.0s: cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq /s...  Sun Nov 26 09:45:45 2006

1000000
1000000

David

---

### Post by rbalfour on 2006-11-26
> **spotslayer said:**
> Results posted below. There is no change. Still running at a throttled speed.



david@DsLNVO:~$ echo performance > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$

Every 1.0s: cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq /s...  Sun Nov 26 09:45:45 2006

1000000
1000000

David

Let's see what you CPU can do?

$ cat /sys/devices/system/cpu/*/cpufreq/scaling_available_governors

As you can see below, this is the out I get from my CPU.

```

userspace ondemand performance

```

So I have the options of these 3. Maybe your CPU has different keywords.

Once you find them then try

```

echo **keyword** > /sys/devices/system/cpu/*/cpufreq/scaling_governor

```

---

### Post by annda on 2006-11-26
hi!

i don't like my cpu throttled either, especially when i don't use the battery. however, scaling_governor gives me "permission denied" but managed to tell me this:

> userspace powersave ondemand conservative performance 

i suppose powersave and conservative are the culprits. is there a way i could change that (considering the permissions problem)?

---

### Post by spotslayer on 2006-11-26
I get the same, but no permission problem. I suppose one line is for each processor. It looks that powersave and conservative are the issue. Is there a config file? I am unable to find one. I don't mind scaling when on battery, but would like to change it when powered. I have used linux before but don't know how to correct this.

david@DsLNVO:~$ cat /sys/devices/system/cpu/*/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance
userspace powersave ondemand conservative performance
david@DsLNVO:~$

David

Forgot to add this. Not sure what it means.

david@DsLNVO:~$ echo powersave > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$ echo conservative > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$

---

### Post by annda on 2006-11-26
so far i've found this:

[http://www.ubuntuforums.org/showthread.php?t=265335](http://www.ubuntuforums.org/showthread.php?t=265335)

i only have laptop-mode-tools installed, no laptop-mode package. changing the configuration file didn't do anything for me. i'll try the other one and post back.

---

### Post by spotslayer on 2006-11-26
Thank's annda. Please keep me posted on your progress. 

David

---

### Post by rbalfour on 2006-11-26
> **spotslayer said:**
> I get the same, but no permission problem. I suppose one line is for each processor. It looks that powersave and conservative are the issue. Is there a config file? I am unable to find one. I don't mind scaling when on battery, but would like to change it when powered. I have used linux before but don't know how to correct this.

david@DsLNVO:~$ cat /sys/devices/system/cpu/*/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance
userspace powersave ondemand conservative performance
david@DsLNVO:~$

David

Forgot to add this. Not sure what it means.

david@DsLNVO:~$ echo powersave > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$ echo conservative > /sys/devices/system/cpu/*/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/*/cpufreq/scaling_governor: ambiguous redirect
david@DsLNVO:~$

can you ls the contents of /sys/devices/system/cpu/

---

### Post by spotslayer on 2006-11-26
Here it is. 

david@DsLNVO:/sys/devices/system/cpu$ ls
cpu0  cpu1
david@DsLNVO:/sys/devices/system/cpu$

david@DsLNVO:/sys/devices/system/cpu/cpu0$ ls
cache  cpufreq  crash_notes  topology
david@DsLNVO:/sys/devices/system/cpu/cpu0$ 

david@DsLNVO:/sys/devices/system/cpu/cpu0/cpufreq$ ls
affected_cpus     ondemand                       scaling_driver    stats
cpuinfo_cur_freq  scaling_available_frequencies  scaling_governor
cpuinfo_max_freq  scaling_available_governors    scaling_max_freq
cpuinfo_min_freq  scaling_cur_freq               scaling_min_freq
david@DsLNVO:/sys/devices/system/cpu/cpu0/cpufreq$

Both directories are identical. I have gone down deeper in the filesystem. Not sure what to do.

David

---

### Post by rbalfour on 2006-11-26
New test pattern

$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

Post back what it outputs.

---

### Post by spotslayer on 2006-11-27
That turned up cpu0. I would like them running at 1667000 when on AC and 1000000 when on battery. To me this looks promising but I am not fluent enough with linux to be sure.

David

Every 1.0s: cat /sys/devices/system/cpu/cpu0/cpufre...  Mon Nov 27 06:44:48 2006

1667000
1000000

---

### Post by rbalfour on 2006-11-27
> **spotslayer said:**
> That turned up cpu0. I would like them running at 1667000 when on AC and 1000000 when on battery. To me this looks promising but I am not fluent enough with linux to be sure.

David

Every 1.0s: cat /sys/devices/system/cpu/cpu0/cpufre...  Mon Nov 27 06:44:48 2006

1667000
1000000

Okay now run the same command on the other CPU as shown below.
$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

And both CPU should be running at full speed.

---

### Post by peachy on 2006-11-27
> **rbalfour said:**
> Okay now run the same command on the other CPU as shown below.
$ sudo su
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
$ watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

And both CPU should be running at full speed.
I had the very same problem and I am now running at a nice healthly 2000 Mhz :D

---

### Post by spotslayer on 2006-11-27
Thank's rbalfour!

Is there a config file or something I can edit to set this to work during boot? I would also like to be able to have things run at a battery saving speed when running on battery. Is there any thing I can do to set things up this way?

David

---

### Post by rbalfour on 2006-11-28
> **peachy said:**
> I had the very same problem and I am now running at a nice healthly 2000 Mhz :D

> **spotslayer said:**
> Thank's rbalfour!

Is there a config file or something I can edit to set this to work during boot? I would also like to be able to have things run at a battery saving speed when running on battery. Is there any thing I can do to set things up this way?

David

A polling script could be made or even just a script to switch between the 2,
performance and power-saving.

---

