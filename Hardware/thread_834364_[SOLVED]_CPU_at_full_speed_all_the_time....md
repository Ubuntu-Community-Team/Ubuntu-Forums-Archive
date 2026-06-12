---
title: "[SOLVED] CPU at full speed all the time..."
date: 2008-06-19
forum: Hardware
---

### Post by kripkenstein on 2008-06-19
I just got a new Core 2 Duo, E8400, and put Hardy on it. Runs great, the only problem I'm having is the CPU is always running at full speed, that is, frequency scaling isn't working.

I tried both powernowd and cpufreqd, neither work. cpufreq-info gives
```

$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```
Running powernowd directly gives
```

/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.

```
and, indeed, there are no such directories. It's as if the CPU's frequency scaling capabilities aren't recognized by Ubuntu...

Any ideas?

(I have a Gigabyte EP35-DS3L motherboard, if that's important.)

---

### Post by sdennie on 2008-06-19
Can you post the output of:

```

lsmod | grep freq

```

---

### Post by kripkenstein on 2008-06-19
Thanks for the response, vor. Here is what I get:
```

$ lsmod | grep freq
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 

```

---

### Post by sdennie on 2008-06-19
Have you tried:

```

sudo modprobe acpi-cpufreq

```

If that doesn't work, it's possible that your motherboard doesn't properly support frequency scaling under linux.  You could try using a newer kernel or see if the DSDT for your motherboard can be fixed (not trivial to do).

---

### Post by kripkenstein on 2008-06-19
> **vor said:**
> Have you tried:

```

sudo modprobe acpi-cpufreq

```


I get
```

$ sudo modprobe acpi-cpufreq
FATAL: Error inserting acpi-cpufreq (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

```
What is very strange however, is that when I looked for the file, I found this:
```

$ locate acpi-cpufreq.ko
/lib/modules/2.6.24-**16**-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko

```
- the file exists, but for the -16 kernel, and I am running the latest kernel, -19. Might that be the problem, that the -19 kernel is missing something?

> 
If that doesn't work, it's possible that your motherboard doesn't properly support frequency scaling under linux.  You could try using a newer kernel or see if the DSDT for your motherboard can be fixed (not trivial to do).

Trying a newer kernel sounds a little beyond my skills at this point... and I don't even know what DSDT means :(

---

### Post by wootah on 2008-06-19
> **kripkenstein said:**
> I just got a new Core 2 Duo, E8400, and put Hardy on it. Runs great, the only problem I'm having is the CPU is always running at full speed, that is, frequency scaling isn't working.

...

May I ask why you want the CPU scaled?

---

### Post by sdennie on 2008-06-19
Some googling makes me think this is a fairly common problem with some Gigabyte motherboards.  Have you enabled "Cool and Quiet" in the motherboards BIOS (assuming that option is available).

---

### Post by kripkenstein on 2008-06-19
> **wootah said:**
> May I ask why you want the CPU scaled?
Well, with frequency scaling the CPU only works at 100% speed when it has to. So this both saves electricity and makes the computer less noisy (the fan can work slower).

> **vor said:**
> Some googling makes me think this is a fairly common problem with some Gigabyte motherboards.  Have you enabled "Cool and Quiet" in the motherboards BIOS (assuming that option is available).
Cool'n'Quiet is an AMD option, as far as I know, and I'm using an Intel Core 2 Duo. I did check very carefully in my BIOS if there were any options that seem related to this issue, and I can't see anything.

---

### Post by kripkenstein on 2008-06-20
Ok, this is now solved.

Turns out it wasn't an Ubuntu issue at all. It's a bug with my motherboard. For some reason the "EIST" option vanishes sometimes in the BIOS screens, and it turns out EIST is Enhanced Intel SpeedStep, and SpeedStep is exactly what is needed to scale CPU frequencies...

By chance I was comparing my BIOS settings to the manual, and I saw that the EIST option was missing. Despite the name seeming to be irrelevant, I Googled it and found it was likely the issue. Anyhow, to get it to appear again I had to fiddle with some other BIOS settings. Long story short, I now have CPU frequency scaling but my memory speed might be a tad lower. But I can live with that.

Thanks again to the people helping out in this thread, I appreciate the effort, it saved me a lot of time.

---

### Post by wootah on 2008-06-20
> **kripkenstein said:**
> Ok, this is now solved.

Turns out it wasn't an Ubuntu issue at all. It's a bug with my motherboard. For some reason the "EIST" option vanishes sometimes in the BIOS screens, and it turns out EIST is Enhanced Intel SpeedStep, and SpeedStep is exactly what is needed to scale CPU frequencies...

By chance I was comparing my BIOS settings to the manual, and I saw that the EIST option was missing. Despite the name seeming to be irrelevant, I Googled it and found it was likely the issue. Anyhow, to get it to appear again I had to fiddle with some other BIOS settings. Long story short, I now have CPU frequency scaling but my memory speed might be a tad lower. But I can live with that.

Thanks again to the people helping out in this thread, I appreciate the effort, it saved me a lot of time.

Could you mention what BIOS setting it was that you changed ?

---

### Post by kripkenstein on 2008-06-20
> **wootah said:**
> Could you mention what BIOS setting it was that you changed ?

It was "CPU EIST Function". When this is enabled, SpeedStep is active and frequency scaling is possible.

---

### Post by chanfle on 2008-06-29
> **kripkenstein said:**
> It was "CPU EIST Function". When this is enabled, SpeedStep is active and frequency scaling is possible.

hi all
I have the same problem some times my laptop acer 5050 use full spped CPU...
I installed DSDT...
any comments??
regards

---

### Post by kripkenstein on 2008-06-29
> **chanfle said:**
> hi all
I have the same problem some times my laptop acer 5050 use full spped CPU...
I installed DSDT...
any comments??
regards

As it's a laptop, I suspect the issue is completely different than the one in this thread. I suggest that you open a new thread so that other people will notice it and help you, they might not see you posting in this one.

---

