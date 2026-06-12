---
title: "Ubuntu 14.04, ASUS Max VI Hero, 4770k stuck at 801mhz max."
date: 2014-05-20
forum: Hardware
---

### Post by Zennmaster on 2014-05-20
Hi All - 

I've been working on this for a few days, with no luck.

I can't seem to figure out how to get this guy over 801Mhz.

I've got Trusty installed on a new, bare metal setup, dual booting with Win7 off of separate SSDs.

Like it says in the subject, the motherboard is an ASUS Maximus VI Hero, and the CPU is an Intel 4770k, 3.5Ghz (3.9 turbo) Overclocked in the BIOS to 4.1 Ghz.

It works just fine in Windows at the OC frequency.

cpufreq-info returns this, which I'm pretty sure is related to the problem:

```
...
analyzing CPU 7:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 7
  CPUs which need to have their frequency coordinated by software: 7
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 801 MHz
  available frequency steps: 801 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 801 MHz and 801 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 801 MHz.
  cpufreq stats: 801 MHz:99.95%, 800 MHz:0.05%  (3)
```

The avalable frequency steps, as well as the hardware limits look awfully strange to me.

Also this:

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
801000 800000 
801000 800000 
801000 800000 
801000 800000 
801000 800000 
801000 800000 
801000 800000 
801000 800000 
```


It seems obvious that I can't go any faster because somehow the limits have been set awfully low.  I really don't think this is a case of the governor being set incorrectly.  It looks more like something just isn't configured right, and I don't feel comfortable just plugging in values.

Interestingly, when I'm running a high-CPU task, such as Handbrake, i7z shows "Actual freq" for each core as being close to the OC value, but still shows "True Frequency" at 800Mhz.  The overall performance, though, is almost the same as I get on my older machine, which is an i7 920 at 2.67Mhz, which also makes me suspicious.  in any case, it would also sure be nice to be able to set a governor to something that had more than 800 and 801Mhz as it's only two options! :)

This is really frustrating, if anyone has any idea, I'd sure appreciate it!

Thanks in advance,

-Michael

---

### Post by Yellow Pasque on 2014-05-21
If you leave BIOS at stock settings, do you still have the issue?

---

### Post by Zennmaster on 2014-05-21
> **Temüjin said:**
> If you leave BIOS at stock settings, do you still have the issue?

Thanks very much for the help!

As it turns out, upgrading the kernel to 3.14.4 seems to have done the trick.

I guess when I was pulling out all that hair, some brain came along with it... :)

---

### Post by Zennmaster on 2014-05-21
> **Zennmaster said:**
> 

As it turns out, upgrading the kernel to 3.14.4 seems to have done the trick.

I guess when I was pulling out all that hair, some brain came along with it... :)

For anyone Googling this in the future, the issue seemed to be caused by having the 

acpi-cpufreq

driver active.  Switching to 

intel_pstate

Appears to be the magic bullet.

---

