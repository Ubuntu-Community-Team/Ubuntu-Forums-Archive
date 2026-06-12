---
title: "Speedstep stuck on 800MHz"
date: 2009-02-14
forum: Hardware
---

### Post by hwinkler on 2009-02-14
For some time after starting up Intrepid on this Dell Precision m2400 laptop, all works normally. I use the cpufreq applet and sensors applet to show speed and temperature. Temperature pretty much remains < 75C so should not be an issue. I can see the CPU in ondemand mode varying between 800 Hz and 2.54 GHz as normal. 

After some time the CPU can become stuck at 800MHz. I cannot use cpufreq applet any longer to change the governor or set it to a certain speed.

This happens frequently when I am running VirtualBox. I'm unsure whether that correlates 100%, but the surest way to get this to happen is for me to run our software unit tests against a db running in a VB guest. I do believe this happens also when I am not running VB, but I don't have a firm case yet. 

I thought the behavior might be related to suspend to RAM, but at this very moment as I type, this computer is stuck in 800MHz but has not been suspended since the last reboot.

I run the powernowd. I have tried switching to cpufreqd but I see the same behavior.

This computer has the intel T9400. 

Here is some diagnostic output. I try to set the cpu speed uppper limit to 2.53 GHz but the cpufreq-info shows it is still at 800 to 800. I've tried many possible params to cpufreq-set, but  nothing changes.

```

hughw@hw2400:~$ sudo cpufreq-set -u 2.53GHz
hughw@hw2400:~$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.54 GHz
  available frequency steps: 2.54 GHz, 2.53 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.54 GHz
  available frequency steps: 2.54 GHz, 2.53 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.


```

Thanks if anyone can help -- if there's any better diagnostics I can run, please suggest. 

Hugh

---

### Post by sdennie on 2009-02-14
I've seen a CPU get stuck at 800Mhz before and the way that I was able to fix it was:

```

sudo cpufreq-selector userspace
sudo cpufreq-selector ondemand

```

It's worth trying at the very least.

---

### Post by hwinkler on 2009-02-28
Son of a gun! That just now worked! Thanks sdennie!

Just to document some other progress I've made in diagnosing (with assistance from Canonical support): Starting the kernel (2.6.27-11-generic ) with parameter acpi=off looks like it fixed the problem (if you can live w/o acpi).

Here is some interesting output from kern.log:

Feb 26 13:08:50 hw2400 kernel: [ 0.488763] ACPI: EC: Look up EC in DSDT
Feb 26 13:08:50 hw2400 kernel: [ 0.488948] ACPI: BIOS _OSI(Linux) query ignored
Feb 26 13:08:50 hw2400 kernel: [ 0.488950] ACPI: DMI System Vendor: Dell Inc.
Feb 26 13:08:50 hw2400 kernel: [ 0.488951] ACPI: DMI Product Name: Precision M2400
Feb 26 13:08:50 hw2400 kernel: [ 0.488953] ACPI: DMI Product Version:
Feb 26 13:08:50 hw2400 kernel: [ 0.488954] ACPI: DMI Board Name: 0HT029
Feb 26 13:08:50 hw2400 kernel: [ 0.488955] ACPI: DMI BIOS Vendor: Dell Inc.
Feb 26 13:08:50 hw2400 kernel: [ 0.488956] ACPI: DMI BIOS Date: 12/17/2008
Feb 26 13:08:50 hw2400 kernel: [ 0.488957] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
Feb 26 13:08:50 hw2400 kernel: [ 0.488958] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]

However, using acpi_osi=Linux did not solve the problem.

Thanks again,

Hugh

---

### Post by utkjamie on 2009-03-08
> **hwinkler said:**
> Just to document some other progress I've made in diagnosing (with assistance from Canonical support): Starting the kernel (2.6.27-11-generic ) with parameter acpi=off looks like it fixed the problem (if you can live w/o acpi).

Thanks for the info! I've been having this problem lately with my computer dropping down to 600MHz when I am in the middle of doing something and then not going back up to full speed for 20 minutes or so. I used to have this problem in Edgy or Feisty but it hasn't been a problem until recently. Turning off SpeedStep in the BIOS causes the CPU to run at a lower speed all the time. I'll try the acpi=off and see what happens.

---

### Post by utkjamie on 2009-03-08
Maybe I did something wrong but using *acpi=off* as a kernel parameter does not work. If anything, the computer seems to be permanently stuck in unusably slow mode.

---

### Post by hwinkler on 2009-03-09
OK ultimately acpi=off did not work, and neither did the cpufreq-selector trick. That seemed to work once, but not subsequently.

It turns out to be a hardware issue. I was able to boot Windows and demonstrate the problem. linux is off the hook.

Dell support thinks it's an unseated heat sink. Parts on the way.

Diagnosing this problem has been chock full 'o red herrings... I think this will fix the problem.

---

### Post by jsalvata on 2009-12-03
Thanks to hwinkler's message above I could establish that my problem (with exactly the symptoms described here) was indeed related to temperature. I called Dell support and received the same diagnostic. Today they sent a technician who preferred to replace the whole main board rather than just the heat sink.

I've now had two CPU-hungry "while :; do :; done" loops running for about 2h while I did my usual CPU-heavy work. The room feels warmer, but the problem has not reappeared.

Kudos to hwinkler for the tip and to Dell Pro Support for their excellent service on this one.

---

