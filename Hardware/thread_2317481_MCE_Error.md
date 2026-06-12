---
title: "MCE Error"
date: 2016-03-16
forum: Hardware
---

### Post by arjan1995 on 2016-03-16
Hi, 

My system has some stability issues.
I use Ubuntu for Android development and am sometimes facing Android emulator crashes.
They'll usually end up as Segmentation Fault in the kern.log like this example:

```
Mar 14 17:13:33 arjan-Z97-HD3 kernel: [ 3238.432267] emulator64-x86[4563]: segfault at fffffffe02c670d0 ip 0000000000487ad0 sp 00007ffca9bc5700 error 5 in emulator64-x86[400000+51d000]

```

This evening another error was logged: 
```

Mar 16 22:53:41 arjan-Z97-HD3 kernel: [ 3456.621370] mce: [Hardware Error]: Machine check events logged

```
In the file mcelog is the following content: 
```
mcelog: failed to prefill DIMM database from DMI data
Hardware event. This is not a software error.
MCE 0
CPU 1 BANK 0 
TIME 1458165221 Wed Mar 16 22:53:41 2016
MCG status:
MCi status:
Corrected error
Error enabled
MCA: Internal parity error
STATUS 90000040000f0005 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 60

```

What is all this error stuff and how do I prevent it? 
Is it true that MCE error is hardware fault?
I switched from Windows to Ubuntu for Android development also due to instability issues ("Display driver stopped responding" sometimes when launching / using Android emulator or emulator only having black screen) 
I hope to get better stability and to be able to continue developing Android apps.

My System:
Ubuntu 14.04 LTS 64-bit
Memory: 7.7 GiB (8GB)
Processor: Intel Core i5 4690 3.5ghz (not overclocked)
Graphics: Amd R9 290 (not overclocked, using open source standard drivers Gallium 0.4 on AMD HAWAII )
Disk: Crucial Mx100 ssd 256gb (~64gb for ubuntu, rest for Windows 10)

Greetings,

Arjan

The Netherlands

---

