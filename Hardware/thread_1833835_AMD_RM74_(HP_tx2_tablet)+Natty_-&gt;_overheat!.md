---
title: "AMD RM74 (HP tx2 tablet)+Natty -&gt; overheat!"
date: 2011-08-26
forum: Hardware
---

### Post by diasf on 2011-08-26
Hi all,

I'm one of the unfortunate owners of the HP tx2 1050 tablet, running on an AMD RM74. This tablet is known for overheating problems. To be able to use it on windows, i'm undervolting and underclocking (550/1100/2200 -> 550/1000/1800) using K10stat. It's a pain, but at least it isn't reaching 100C anymore (on a cold boot, he reaches 90C before I can turn K10 on).

Now on to Natty.
I've configured cpufreqd to not let the cpu burn, it's working like a charm. However, on windows, while stuck on 550Mhz, he stays around 50C. Right now, also stuck on 550Mhz, 65C. So I went on to try to undervolt/underclock...

I followed this guide:
[http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html](http://linuxsolver.blogspot.com/2011/02/undervolting-cpu-in-ubuntu.html)
To install the phc kernel (ppa, reboot, etc).
However, when I change the phc_vids, nothing changes. 
So, does the last phc kernel supports RM74?
Is there any other option? AFAIK, the processor is running some on 0.2v than it should...

Thanks in advance..
ps: You even tried running Unity on a 550Mhz pc? Don't....

---

### Post by diasf on 2011-08-29
By the way, pwmconfig isn't working either.... the only sensor i can pick up is the processor, no fan, no nothing.
If I could speed the cooler up a bit, i would spend less time on 500mhz.... anyone?

---

### Post by Favux on 2011-08-29
Hi diasf,

Welcome to Ubuntu forums!

You could try the acpi_osi fix described here:  [http://ubuntuforums.org/showthread.php?t=1709127&page=2](http://ubuntuforums.org/showthread.php?t=1709127&page=2)

Someone also mentioned that the kernel power fix cooled their laptop down significantly too:  [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by diasf on 2011-08-30
thx, for the reply!

Did both, no change. Still cant undervolt, pwmconfig isnt finding any sensors, sensors itself didn't change (i ran sensors-detect, got only what seems to be processor and north bridge). The current temperature didn't change either. Basically, nothing changed :(

Ideally, I would like to undervolt it and speed up the cooler a little bit. I have a ventilation system for when i'm home, but can't walk around with it...

Thanks again for the reply...

---

### Post by diasf on 2011-08-31
Turns out, i'm stupid...
AMD uses increasing VIDs for decreasing voltages.... phd is working fine. Didn't get much less temperature than before, but it&#347; working.... marked as solved, cheers for the help, sorry for the stupidity...

---

