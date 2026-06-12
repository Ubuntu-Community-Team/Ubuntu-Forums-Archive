---
title: "Processor speed limited after suspend in 15.10."
date: 2016-03-05
forum: Hardware
---

### Post by Aisteru on 2016-03-05
I just noticed today that my CPU frequency is limited when I wake my computer from suspend. The maximum CPU speed is set to 3.10 GHz when I first boot, but is 2.48 GHz after suspending an waking the system. This drops again after each suspend, bottoming out at 1.24 GHz.

The same thing happens with either intel_pstate enabled or the older acpi-cpufreq, but the numbers are different: with intel_pstate the numbers are 3.10 GHz, 2.48 GHz, 1.86 GHz, and 1.24 GHz., but with acpi-cpufreq the numbers are 2.5 GHz, 2 GHz, 1.5 GHz, 1 GHz, as reported by cpufreq-info. This would mean that it is falling by .62 GHz with one driver, and by .5 GHz with the other. I don't know if this could be important.

When using the acpi_cpufreq driver, unlike when using intel_pstate, the maximum when first booted is set at 1.5GHz. This can be changed by using cpufreq-set, but after suspending it drops as described above, and cpufreq-set cannot raise it.

Can anyone clue me in as to what might be lowering the CPU speed? Any help would be appreciated.

---

### Post by Doug S on 2016-03-05
I have heard of this [before]("http://askubuntu.com/questions/740108/strange-cpufreq-scaling-issues-cant-permanently-force-performance-governer-and"), but don't know the root issue.

While running with the intel_pstate frequency scaling governor, and while you have the issue could you do these commands and provide the output for your computer:
```
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_max_freq[/COLOR]
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_min_freq[/COLOR]
1600000
1600000
1600000
1600000
1600000
1600000
1600000
1600000
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq[/COLOR]
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
doug@s15:~$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpufreq/policy*/scaling_min_freq[/COLOR]
1600000
1600000
1600000
1600000
1600000
1600000
1600000
1600000
doug@s15:~$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:42
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:23
/sys/devices/system/cpu/intel_pstate/turbo_pct:18
doug@s15:~$ sudo modprobe msr
doug@s15:~$ [COLOR="#FF0000"]sudo rdmsr -a 0x19a[/COLOR]  <<< you needs msr-tools package for this one.
0
0
0
0
0
0
0
0
doug@s15:~$

```

---

### Post by Aisteru on 2016-03-06
This is what I got:

```

timmy@unicorn:~$ cat /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_max_freq
cat: /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_max_freq: No such file or directory
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_min_freq
cat: /sys/devices/system/cpu/cpufreq/policy*/cpuinfo_min_freq: No such file or directory
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq
cat: /sys/devices/system/cpu/cpufreq/policy*/scaling_max_freq: No such file or directory
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpufreq/policy*/scaling_min_freq
cat: /sys/devices/system/cpu/cpufreq/policy*/scaling_min_freq: No such file or directory
timmy@unicorn:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/max_perf_pct:80
/sys/devices/system/cpu/intel_pstate/min_perf_pct:25
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:24
/sys/devices/system/cpu/intel_pstate/turbo_pct:25
timmy@unicorn:~$ sudo modprobe msr
[sudo] password for timmy: 
timmy@unicorn:~$ sudo rdmsr -a 0x19a
8
8
8
8
timmy@unicorn:~$ 


```

After poking around looking for the missing files, I discovered I have no /sys/devices/system/cpu/cpufreq/policy* folders. Inside /sys/devices/system/cpu/ I find what seems to be a directory for each virtual core (amoung other things,) but none of those have policy directories. The closest I could come to matching what you asked for was:

```

timmy@unicorn:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_max_freq 
3100000
3100000
3100000
3100000
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_min_freq
800000
800000
800000
800000
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq
2480000
2480000
2480000
2480000
timmy@unicorn:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_min_freq
800000
800000
800000
800000
timmy@unicorn:~$ 

```

---

### Post by Doug S on 2016-03-06
re: no policy directory: I guess 15.10 still has an older version of the intel_pstate driver. Sorry, I thought it was up to date.

I do not know why or how /sys/devices/system/cpu/intel_pstate/max_perf_pct gets set to 80%. You can set it back via:

```
echo "100" | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

While you are reading an odd value from the clock modulation register (19A), it is disabled (which is good).

Your numbers seem to indicate max_perf_pct goes from 100% to 80% to 60% to 40% with each subsequent suspend. Could you confirm?

When running with the acpi-cpufreq frequency scaling driver, and when stuck at 1.5 GHz, what do you get reading register 19A?

What is the make and model of your computer?

---

### Post by Aisteru on 2016-03-06
I tried
```


echo "100" | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct


```

but when I used 'cat' to read the value, it printed '80' 

You are correct, max_perf_pct does go from 100% to 80% to 60% to 40% with each subsequent suspend.

When running with the acpi-cpufreq frequency scaling driver, I get the same results from the 'rdmsr -a 0x19a' command as before:
```

root@unicorn:~# rdmsr -a 0x19a
8
8
8
8

```

And lastly, the computer in question is a Lenovo g510 Laptop.

---

### Post by Doug S on 2016-03-07
> **Aisteru said:**
> the computer in question is a Lenovo g510 Laptop.The other similar case is Lenovo also. I wonder about a BIOS issue.

Are you running any thermal daemon, such as thermald or tlp or whatever? If yes, could you try to disable, just as a test.

---

### Post by Aisteru on 2016-03-08
It hadn't started causing noticeable problems until recently, but I guess it could be a BIOS issue.

Thermald was running, but stopping it didn't seem to change the behavior. If I understood better what was going on when I hit suspend, I'd have a better idea of where to look for the cause. I suspect there is something wrong with the suspend-time scripts, but I don't know where to look; when I tried researching suspend-related issues before, i didn't have much luck finding up-to-date information on what goes on under the hood.

---

### Post by Doug S on 2016-03-09
> **Aisteru said:**
> It hadn't started causing noticeable problems until recently, but I guess it could be a BIOS issue.Could you go back and try a previous kernel? You could also try [the most recent release candidate kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc7-wily/"), to see if the issue is fixed.

> **Aisteru said:**
> If I understood better what was going on when I hit suspend, I'd have a better idea of where to look for the cause. I suspect there is something wrong with the suspend-time scripts, but I don't know where to look; when I tried researching suspend-related issues before, i didn't have much luck finding up-to-date information on what goes on under the hood.Is there anything in the /var/log directory? You could also suspend and resume manually, and see if there is anything in the /var/log/pm-suspend.log file.

---

### Post by Aisteru on 2016-03-09
> **Doug S said:**
> Could you go back and try a previous kernel? You could also try [the most recent release candidate kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.5-rc7-wily/"), to see if the issue is fixed.

Wow! I tried an older kernel (I think it's 4.2.0-19-lowlatency) and now  things seem to be back as they should be, at least as far as this issue. Thank you so much for all the help! :D\\:D/

> **Doug S said:**
> Is there anything in the /var/log directory? You could also suspend and resume manually, and see if there is anything in the /var/log/pm-suspend.log file.

I did see a lot of information in /var/log/pm-suspend.log about the suspend/hibernate scripts, so thanks for pointing that out as well. 

I'm going to mark this thread as solved.

I wonder if you could shed some light on my other problem? [http://ubuntuforums.org/showthread.php?t=2315306](http://ubuntuforums.org/showthread.php?t=2315306) I don't mean to impose, but no one has offered any ideas yet.

---

### Post by Doug S on 2016-03-09
What is the problematic kernel version? (I want to mention it on that other thread.)
If interested, you could continue to help with this issue by trying the current 4.5-rc7 kernel and by filing a bug report if it still has the issue. The next step would be to bisect the kernel to isolate the offending commit.

Did you try the older kernel for your other thread? Otherwise, I don't have a suggestion for it.

---

### Post by Aisteru on 2016-03-09
The weird throttling happens with kernel version 4.2.0-30-lowlatency.

I've had the other problem since I got this computer I think, and that was in 2014, so I've tried many kernels, and several releases of Ubuntu. I'll check to see if i can find anything revealing in the log, but I don't think I had any luck with that before.

---

### Post by Aisteru on 2016-03-10
I tried the kernel linux-image-4.5.0-040500rc7-lowlatency_4.5.0-040500rc7.201603061830_amd64.deb, and it seems to have the same problem with throttling. :roll:

---

### Post by Linuxisfast on 2016-03-10
> **Doug S said:**
> What is the problematic kernel version? (I want to mention it on that other thread.)
If interested, you could continue to help with this issue by trying the current 4.5-rc7 kernel and by filing a bug report if it still has the issue. The next step would be to bisect the kernel to isolate the offending commit.

Did you try the older kernel for your other thread? Otherwise, I don't have a suggestion for it.


Could this be related to the same issue Arch kernels suffer with 300Hz config and Intel Haswell, someone also reported this with new Skylake as well. Just a thought.

---

### Post by Doug S on 2016-03-11
> **Linuxisfast said:**
> Could this be related to the same issue Arch kernels suffer with 300Hz config and Intel Haswell, someone also reported this with new Skylake as well. Just a thought.I do not think so. The specific symptoms here are different.

I have looked for a relevant bug report on launchpad, but didn't find anything (which doesn't mean it doesn't exist, just that if it does I didn't find it). I still think the next step is to bisect the kernel, but that is a lot of work and Aisteru might not be willing to go down that path.

In my opinion / recollection, the 300Hz kernel thing was a red herring. It just so happened to increase the probability of manifestation of an issue that was actually present on all HZ rates,  because of a beat frequency between the frame rate and the 300Hz. See also [here]("https://bugzilla.kernel.org/show_bug.cgi?id=93521#c42").

---

### Post by Linuxisfast on 2016-03-11
> **Doug S said:**
> I do not think so. The specific symptoms here are different.

I have looked for a relevant bug report on launchpad, but didn't find anything (which doesn't mean it doesn't exist, just that if it does I didn't find it). I still think the next step is to bisect the kernel, but that is a lot of work and Aisteru might not be willing to go down that path.

In my opinion / recollection, the 300Hz kernel thing was a red herring. It just so happened to increase the probability of manifestation of an issue that was actually present on all HZ rates,  because of a beat frequency between the frame rate and the 300Hz. See also [here]("https://bugzilla.kernel.org/show_bug.cgi?id=93521#c42").


I have been following that thread, however the issue persists, the temp stays high under Arch and so does Vcore as compared to Ubuntu or Fedora. Currently on 14.04.4 LTS with kernel 4.2 and temps especially under load stays lower by 2 degrees C as opposed to Arch with latest 4.4 kernel.

---

### Post by Doug S on 2016-03-15
Please also see, and possibly contribute to, [here]("https://bugzilla.kernel.org/show_bug.cgi?id=114551")

---

