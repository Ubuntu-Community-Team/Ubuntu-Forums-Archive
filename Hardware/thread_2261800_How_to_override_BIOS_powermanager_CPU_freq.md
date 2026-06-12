---
title: "How to override BIOS powermanager CPU freq"
date: 2015-01-21
forum: Hardware
---

### Post by erik-vanlier on 2015-01-21
Hi there,

I have a Toshiba C50-B-14Z with Ubuntu Mate 14.04.1. All works flawlessly so that's nice, except 1 thing:

When I disconnect the powercable the CPUfreq falls back to 850 Mhz... instead of the 2.2Ghz. Is there a way to keep the cpufreq on performance?
The tools I know don't work. The only option I have in BIOS is to keep the CPUfreq always low.... and that's not what I want.

Intel 2840 CPU

Erik

---

### Post by Yellow Pasque on 2015-01-22
So are you saying that the CPU is not scaling on demand when it's running on battery (i.e. never goes above 850 MHz even with a demanding task), or do you just want the CPU to run at full speed all the time because you think it'll be noticeably faster?

---

### Post by erik-vanlier on 2015-01-22
That's correct, I cannot scale on my demand or task demand, ánd I want to run at full speed. It is noticeable... right?

---

### Post by Yellow Pasque on 2015-01-22
[https://github.com/torvalds/linux/commit/2f86dc4cddcb21290ca099e1dce2a53533c86e0b](https://github.com/torvalds/linux/commit/2f86dc4cddcb21290ca099e1dce2a53533c86e0b)

In other words, try the latest kernel: 
[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc5-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc5-vivid/)

---

### Post by erik-vanlier on 2015-01-23
Thnx! That did the job. At least the CPU works on task demand, even to full turbo. Still can't manual adjust to max performance but that's OK. I used the 3.19RC5 Vivid version.
Thnx again!

---

### Post by Yellow Pasque on 2015-01-23
You're welcome. It sounds like manual control is still possible:
> In addition to the interfaces provided by the cpufreq core for controlling frequency the driver provides sysfs files for controlling P state selection. These files have been added to /sys/devices/system/cpu/intel_pstate/

---

### Post by erik-vanlier on 2015-01-23
That's correct, I can choose between Performance or Powersave.

---

### Post by erik-vanlier on 2015-01-24
..... however.... 3.19RC5 is buggy, lots of noise from the inside of the laptop (???), bluetooth bugs, Intel thread bug... etc... I sit and wait and went back to 3.13 until 3.19 is bugfree. But it worked!

---

