---
title: "Powernowd isn't working after boot"
date: 2010-06-23
forum: Hardware
---

### Post by Illuvata on 2010-06-23
Hello,

I'm relatively new with ubuntu.
I've tried to trig the frequency of my Toshiba A60-120. Here is the cpufreq-info after a reboot:
```

famille@famille-laptop:~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Veuillez rapportez les erreurs et les bogues à cpufreq@vger.kernel.org, s'il vous plait.
analyse du CPU 0 :
  pilote : p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  limitation matérielle : 367 MHz - 2.93 GHz
  plage de fréquence : 367 MHz, 733 MHz, 1.10 GHz, 1.47 GHz, 1.83 GHz, 2.20 GHz, 2.57 GHz, 2.93 GHz
  régulateurs disponibles : conservative, ondemand, userspace, powersave, performance
  tactique actuelle : la fréquence doit être comprise entre 367 MHz et 2.93 GHz.
                  Le régulateur "performance" est libre de choisir la vitesse
                  dans cette plage de fréquences.
  la fréquence actuelle de ce CPU est 2.93 GHz.
  des statistique concernant cpufreq:367 MHz:0,00%, 733 MHz:0,00%, 1.10 GHz:0,00%, 1.47 GHz:0,00%, 1.83 GHz:0,00%, 2.20 GHz:0,00%, 2.57 GHz:0,00%, 2.93 GHz:100,00%

```

Sorry, it's in French. 

As you could see, the actual governor is "performance" even if I've already installed the powernowd package (I choose this package because cpufreqd doesn't work on my laptop.

Now if I type :
```
famille@famille-laptop:~$ sudo powernowd
[sudo] password for famille: 
powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 366Mhz - 2933Mhz (8 steps)
```

and with a new cpufreq-info :
```
famille@famille-laptop:~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Veuillez rapportez les erreurs et les bogues à cpufreq@vger.kernel.org, s'il vous plait.
analyse du CPU 0 :
  pilote : p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  limitation matérielle : 367 MHz - 2.93 GHz
  plage de fréquence : 367 MHz, 733 MHz, 1.10 GHz, 1.47 GHz, 1.83 GHz, 2.20 GHz, 2.57 GHz, 2.93 GHz
  régulateurs disponibles : conservative, ondemand, userspace, powersave, performance
  tactique actuelle : la fréquence doit être comprise entre 367 MHz et 2.93 GHz.
                  Le régulateur "userspace" est libre de choisir la vitesse
                  dans cette plage de fréquences.
  la fréquence actuelle de ce CPU est 1.83 GHz.
  des statistique concernant cpufreq:367 MHz:17,14%, 733 MHz:0,06%, 1.10 GHz:0,21%, 1.47 GHz:1,80%, 1.83 GHz:0,02%, 2.20 GHz:0,13%, 2.57 GHz:0,49%, 2.93 GHz:80,15%  (18)
```

The governor is "userspace" and the frequency is different.

In the /etc/default/powernowd file, I've put OPTION="-q -m 2".

I woul'd like that powernowd works directely after a boot, how can I do that ?

thanks.

---

### Post by dino99 on 2010-06-23
actual kernels deals directly with powersaving, and these packages (yours above) are not used nowadays in most cases.

Instead you need to install the specific toshiba packages (search "tosh" into synaptic) installed and laptop-mode-tools, hwinfo too

---

### Post by Illuvata on 2010-06-23
Thank you for your answer. Do I have to remove frequtils sysfsutils and powernowd packages ?

---

### Post by Illuvata on 2010-06-23
I've tried toshset an toshutils packages, but they don't worked because after some researches on the net, it seems that my BIOS isn't compatible with toshset. So, if somebody could answer to my first question : How get powernowd Daemon running after boot ?

thank you !

---

### Post by Illuvata on 2010-06-24
up

---

### Post by glennr on 2012-01-12
I also have this issue on 10.04. Any solutions?

---

### Post by jdackle on 2012-01-21
Bumped into this while looking for an answer myself and I think I got it now! :D

NB: I am not currently using Ubuntu but rather Debian 6.0.3 (stable).

The 'cpufreq-info' command comes with the cpufrequtils .deb package. So if your setup is like mine on Debian, you will have the **/etc/init.d/cpufrequtils** file containing this line:```
GOVERNOR="**ondemand**"
```The thing is powernowd requires GOVERNOR="**userspace**" to be loaded instead.

So the simple solution would be to just edit that file and do the apropriate correction. But a more sane sollution is to simply drop that line to a different file instead: **/etc/default/cpufrequtils**:```
echo GOVERNOR=\"userspace\" >/etc/default/cpufrequtils
```(as user **root** of course)
Note:I did not have this file installed on my system, so there was no problem in doing it that way. But if you do already have that file, that command will overwrite it! In that case, or if you just prefer to, you'd better edit /etc/default/cpufrequtils and do the apropriate edit.

Hope that helps! :)

---

