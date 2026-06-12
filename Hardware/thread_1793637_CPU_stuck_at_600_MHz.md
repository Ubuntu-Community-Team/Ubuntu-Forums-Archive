---
title: "CPU stuck at 600 MHz"
date: 2011-06-29
forum: Hardware
---

### Post by maulynvia on 2011-06-29
How can I get the (intel centrino) CPU to run at 1.6 GHz?

```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: [COLOR="Red"]acpi-cpufreq[/COLOR]
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: [COLOR="Red"]frequency should be within 600 MHz and 600 MHz.[/COLOR]
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, [COLOR="red"]600 MHz:100.00%[/COLOR]
bears@bears-laptop:~$ 

```

I've tried editing /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq but this seems locked ([see my post here]("http://ubuntuforums.org/showthread.php?t=1792945"))

I've tried
```
laptop:~$ cpufreq-set -u 1600000
Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?
```

Also added ```
CPUFREQ_CPU_MODULE="speedstep-centrino"
``` to ```
/etc/default/cpufreqd
```

The above done with much googling and little understanding - any help much appreciated.

---

### Post by psusi on 2011-06-29
You need to run it with sudo, or just do something that uses the cpu and it will automatically speed up as needed.

---

### Post by maulynvia on 2011-06-30
I have run with sudo and as root and as super user, but it doesn't work. The processor never scales beyond 600 MHz, and e.g. videos are jerky.

---

### Post by psusi on 2011-06-30
Maybe you could post the results of running it with sudo then?

Also you seem to have switched to the powersave governor, which is why it is staying at the minimum.  You normally want to use ondemand.

---

### Post by maulynvia on 2011-07-01
Seems like I am unable to change the governor (even as root). Could this be the problem?

```
root@bears-laptop:/home/bears# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
powersave
root@bears-laptop:/home/bears# echo ondemand >  /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@bears-laptop:/home/bears# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
powersave
root@bears-laptop:/home/bears# cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz (asserted by call to hardware).
  cpufreq stats: 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:100.00%
root@bears-laptop:/home/bears# 
```

---

### Post by psusi on 2011-07-01
Yea, I'd say that's the problem.  That is really weird.

---

### Post by maulynvia on 2011-07-03
Now I discover that I am free to change CPU speed on battery power. As soon as I plugin the mains cable, then it goes straight to minimum speed. What's going on? How do I change this?

---

### Post by maulynvia on 2011-07-03
I think this is a bug,
[https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429](https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429)

---

### Post by psusi on 2011-07-03
> **maulynvia said:**
> I think this is a bug,
[https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429](https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429)

Unrelated.  That person had hardware limiting the top speed.

---

### Post by wojox on 2011-07-03
What does this give you:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
ondemand userspace performance
```

Also try loading all the modules as root:

```
modprobe cpufreq_performance cpufreq_ondemand cpufreq_conservative cpufreq_userspace
```

Then try setting it to on demand:

```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Check it:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

If this is a laptop you really don't want to go over ondemand or you laptop will run extremely hot.

---

### Post by maulynvia on 2011-07-04
Thanks so much for your suggestion. This all seems to work fine *except* that it still says that "[COLOR="red"]current policy: frequency should be within 600 MHz and 600 MHz[/COLOR]". Nothing I do seems to affect this limit (neither stressing the machine when ondemand or manually setting the CPU freq to something higher - unless I switch to battery, and then all is OK.

```
bears@bears-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 
bears@bears-laptop:~$ sudo su -
[sudo] password for bears: 
root@bears-laptop:~# modprobe cpufreq_performance cpufreq_ondemand cpufreq_conservative cpufreq_userspace
root@bears-laptop:~# echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand

root@bears-laptop:~# cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  [COLOR="Red"]current policy: frequency should be within 600 MHz and 600 MHz[/COLOR].
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz (asserted by call to hardware).
  cpufreq stats: 1.60 GHz:0.86%, 1.40 GHz:0.00%, 1.20 GHz:0.48%, 1000 MHz:0.19%, 800 MHz:0.00%, 600 MHz:98.47%  (8)
```

---

### Post by maulynvia on 2011-07-04
Just found something else:

```
root@bears-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold 
95
```

What is this 95 number? Could this be where the limit is coming from?

---

### Post by psusi on 2011-07-05
Ohh, you got it to switch to ondemand now?  Good.  Take a look at the scaling_max_frequency I think it was.

---

### Post by conradin on 2011-07-14
Bump. 
I have this problem too.. Ive tried:
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)
but it doesnt cut it. I also tried reseting the bios.

---

### Post by TBABill on 2011-07-14
I saw the ondemand threshold setting you had looked at but I didn't note anywhere in the thread where the actual governor that decides what speed to use was changed from powersave. With it limiting it to "600 to 600" you may want to try changing the governor setting itself and see what works. 
 
I'd first try "performance" since that keeps your CPU at max, but just as a trial to see if it'll speed up to 1.6 properly. Keeping it there will contribute to higher heat levels. Standard for Ubuntu is to scale via the ondemand governor.
 
To switch governor settings you can:
```
sudo cpufreq-set --governor performance
``` and for ondemand just swap performance for ondemand above.

---

### Post by maulynvia on 2011-07-14
Hi
I can change governor but not the range available to the governor.

I fixed this by reinstalling 10.04. Then I run the updates and the problem is back. :(

---

