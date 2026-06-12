---
title: "CPU freqency monitor doesnt work anymore"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by PeterBurg on 2009-09-29
After upgrading to 9.04 the CPU frequency monitor applet didn't work anymore, after reinstalling I got the following answer.
Seems to me the system didn't recognize the CPU. Can anyone help me to fix this, it works on full speed now:(? 
CPU: AMD Athlon 64 X2 6400+


```
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * disabled, governor not available...                                   [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
peter@wunjo6:~$ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
xxxxxx:~$ dmesg | grep -i power
[    0.000000] ACPI: SSDT 77EEBA40, 0350 (r1 PTLTD  POWERNOW        1  LTP        1)
[   39.764669] input: Power Button (FF) as /devices/virtual/input/input3
[   39.780949] ACPI: Power Button (FF) [PWRF]
[   39.781055] input: Power Button (CM) as /devices/virtual/input/input4
[   39.798909] ACPI: Power Button (CM) [PWRB]
[   41.659832] SetRFPowerState8185(): unknown RFChipID: 0x5!!!

```

---

### Post by PeterBurg on 2009-09-29
Good news: works again after restart:KS
The reinstall did work

---

