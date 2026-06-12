---
title: "Installing CPU Governor for AMD K8 to reduce freq?"
date: 2020-12-05
forum: Hardware
---

### Post by vpmry on 2020-12-05
I need to set a lower frequency ceiling* of my laptop's CPU but I'm having difficulty in doing this. I had no problems doing this on Windows, so I know it is possible on this hardware platform. The CPU in question is an AMD Athlon 64 X2 L310 and is a member of the "K8" microarchitecture family.

I'm new to Debian and Linux in general, but on researching this problem it seems I need to have a CPU governor installed to do this and use cpupower to reduce the frequency. Most of the examples online I see are specific to an Intel platform unfortunately, but I was able to get the "cpupower" package installed. I tried getting cpufreq installed but I'm a bit stuck on what references are missing and I've read that it's supplanted by cpupower anyway. Upon running cpupower though, it says it cannot find any cpu governors. I would very much appreciate some direction here as I'm not sure what to do next. I'm on Ubuntu 20.04. Please help if you can?

Output I get from cpupower: ```

~$ sudo cpupower frequency-info
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  CPUs which run at the same hardware frequency: Not Available
  CPUs which need to have their frequency coordinated by software: Not Available
  maximum transition latency:  Cannot determine or is not supported.
Not Available
  available cpufreq governors: Not Available
  Unable to determine current policy
  current CPU frequency: Unable to call hardware
  current CPU frequency:  Unable to call to kernel
  boost state support:
    Supported: no
    Active: no

```

** The reason I need the frequency reduced is I've upgraded this laptop from a single core to a dual core -- the single core CPU is just not usable for me. Despite sharing the same TDP this laptop just cannot deliver the necessary power to run this dual core processor at full speed and will occasionally hard crash, usually when doing something demanding. When I had Windows installed on it, it worked perfectly well when I set the max frequency 200Mhz lower than stock and I'm looking to repeat the same thing here with Ubuntu.*

---

### Post by mikewhatever on 2020-12-06
You need something called <cpufrequtils>. Once installed, tun <cpufreq-info> to see available frequencies and governors. Use <cpufreq-set> to limit the frequency if a lower one is available. For more info, check the man page <man cpufreq-set>.

---

### Post by vpmry on 2020-12-06
Thanks for the suggestion. Here's what I get with cpufrequtils:

```
~$ sudo cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.


```

```
~$ sudo cpufreq-set -u 1.0Ghz
Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?


```

---

### Post by norobro on 2020-12-06
Try checking your systemd journal to see if there are any clues as to what's going on. ```
~$ journalctl -b --no-pager | grep -i "cpufreq"
Dec 06 16:28:08 Ubuntu kernel: acpi_cpufreq: overriding BIOS provided _PSD data
Dec 06 16:28:11 Ubuntu systemd[1]: Starting LSB: Load kernel modules needed to enable cpufreq scaling...
Dec 06 16:28:11 Ubuntu systemd[1]: Started LSB: Load kernel modules needed to enable cpufreq scaling.
Dec 06 16:28:11 Ubuntu systemd[1]: Starting LSB: set CPUFreq kernel parameters...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:  * CPUFreq Utilities: Setting ondemand CPUFreq governor...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:  * CPU0...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:  * CPU1...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:  * CPU2...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:  * CPU3...
Dec 06 16:28:11 Ubuntu cpufrequtils[717]:    ...done.
Dec 06 16:28:11 Ubuntu systemd[1]: Started LSB: set CPUFreq kernel parameters.
Dec 06 16:28:15 Ubuntu set-cpufreq[685]: Setting ondemand scheduler for all CPUs
```The above is from a machine with an AMD K10 chip.

---

### Post by vpmry on 2020-12-07
I have lots of failures. 

```
Dec 07 14:37:14 LT31 systemd[1]: Starting LSB: start and stop cpufreqd...
Dec 07 14:37:14 LT31 systemd[1]: Starting LSB: Load kernel modules needed to enable cpufreq scaling...
Dec 07 14:37:15 LT31 cpufreqd[607]:  * Starting CPU Frequency daemon cpufreqd
Dec 07 14:37:15 LT31 loadcpufreq[632]:  * Loading cpufreq kernel modules...
Dec 07 14:37:15 LT31 cpufreqd[607]:    ...fail!
Dec 07 14:37:15 LT31 systemd[1]: cpufreqd.service: Control process exited, code=exited, status=1/FAILURE
Dec 07 14:37:15 LT31 systemd[1]: cpufreqd.service: Failed with result 'exit-code'.
Dec 07 14:37:15 LT31 systemd[1]: Failed to start LSB: start and stop cpufreqd.
Dec 07 14:37:15 LT31 loadcpufreq[632]:    ...fail!
Dec 07 14:37:15 LT31 systemd[1]: Started LSB: Load kernel modules needed to enable cpufreq scaling.
Dec 07 14:37:15 LT31 systemd[1]: Starting LSB: set CPUFreq kernel parameters...
Dec 07 14:37:16 LT31 cpufrequtils[760]:  * CPUFreq Utilities: Setting ondemand CPUFreq governor...
Dec 07 14:37:16 LT31 cpufrequtils[760]:  * disabled, governor not available...
Dec 07 14:37:16 LT31 cpufrequtils[760]:    ...done.
Dec 07 14:37:16 LT31 systemd[1]: Started LSB: set CPUFreq kernel parameters.


```

---

### Post by rsteinmetz70112 on 2020-12-07
It looks like cpufreqd.service is not running and possibly needs to be started/configured.
I don't have it installed on my machine so I can't check.
```

cpufreqd.service: Control process exited, code=exited, status=1/FAILURE
cpufreqd.service: Failed with result 'exit-code'.
```

What do you get with :

```
sudo systemctl status cpufreqd
```

---

### Post by norobro on 2020-12-07
You can start the daemon from the command line and get debugging output. See 'man cpufreqd'. Maybe that will give us more info about why it is failing. ```
$ sudo cpufreqd -D -V5
```Using -V6 or -V7 generates a lot of output so if you use either of those switches you probably want to output to a file.```
$ sudo cpufreqd -D -V6 2& > /path/to/somefile
```

---

### Post by vpmry on 2020-12-12
Thanks for the reply you two. Unfortunately not much in specifics with either other than similar "failed to start" messages. I tried a few versions back of ubuntu (to 10.04 at the oldest) using a live version and still no dice. Finally got fed up and just searched online for the specific model number of the laptop (Gateway LT31) and found this: [https://ubuntuforums.org/showthread.php?t=1253365](https://ubuntuforums.org/showthread.php?t=1253365) . Ooph. Pretty dumb of me not to just search for the laptop instead of the CPU arch.

At any rate, really appreciate the assistance of everyone in this thread. I'm going to comb through the one I found and see if there are any solutions for 20.04.

---

