---
title: "CPU scaling doesn't work"
date: 2009-08-24
forum: Hardware
---

### Post by Sean Hayes on 2009-08-24
I installed the GNOME CPU Frequency Scaling Monitor and powernowd, but it says CPU scaling is unsupported. My processor is an AMD Athlon 64 Socket 754 3700+. I haven't found info on whether it's supposed to support it, but when I had Windows installed I was able to create a power plan that reduced the CPU usage. Is there anyway to implement this in Ubuntu?

---

### Post by Sean Hayes on 2009-09-05
*Bump*

Should I post this in another forum section?

---

### Post by Yellow Pasque on 2009-09-05
Linux supports PowerNow/Cool'n'Quiet. The only thing I have installed on my Athlon is cpufreq-utils.

---

### Post by Sean Hayes on 2009-09-08
> **Temüjin said:**
> Linux supports PowerNow/Cool'n'Quiet. The only thing I have installed on my Athlon is cpufreq-utils.

Does this help at all?
```
saints@saints-htpc:~$ sudo cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
```
```
saints@saints-htpc:~$ sudo dmesg | grep -i power
[    2.960814] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.960820] ACPI: Power Button (FF) [PWRF]
[    2.960907] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.960913] ACPI: Power Button (CM) [PWRB]
[    7.211389] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    7.216574] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
```

---

### Post by Yellow Pasque on 2009-09-08
> powernow-k8: BIOS error - no PSB or ACPI _PSS objects
That's not good :( Make sure you have the latest BIOS. If it still doesn't work, your only hope is modifying the DSDT: See: [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

---

