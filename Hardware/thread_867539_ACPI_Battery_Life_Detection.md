---
title: "ACPI Battery Life Detection"
date: 2008-07-23
forum: Hardware
---

### Post by Milyardo on 2008-07-23
I have an ZTSystems L-series Laptop(Don't remember which one, its based on an MSI barebone). I'm having many issues with Ubuntu detecting battery life. The detected battery life varies widely, changing values every couple of seconds% 86%, 3%, 0%, or even 1046%!(how I wish that last one were true :D) Ubuntu will automaticly shut down my laptop after a few minutes from lack of battery life, however if I boot right back into Vista I'll see my battery is still full.

Here's an Example of my battery info from /proc/acpi/battery/BAT1/info

```
zpowers@zilog:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         786 mAh
last full capacity:      49168 mAh
battery technology:      rechargeable
design voltage:          42283 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            MS-1719

serial number:           

battery type:            LION

OEM info:                MSI Corp.

```
My Last full capacity is interesting, something about it tells me its inaccurate :)

To illustrate the changes in battery life I ran the command "echo `date` && cat /proc/acpi/battery/BAT1/state" a couples times. The first run is while my AC Adapter is still plugged in.

```

zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:42:13 EDT 2008
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            769 mA
remaining capacity:      2576 mAh
present voltage:         38961 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:42:22 EDT 2008
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2718 mA
remaining capacity:      4245 mAh
present voltage:         12207 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:42:33 EDT 2008
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2315 mA
remaining capacity:      4239 mAh
present voltage:         12218 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:43:00 EDT 2008
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1527 mA
remaining capacity:      10768 mAh
present voltage:         32047 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:43:09 EDT 2008
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2199 mA
remaining capacity:      4214 mAh
present voltage:         12136 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:43:14 EDT 2008
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2280 mA
remaining capacity:      4212 mAh
present voltage:         12034 mV
zpowers@zilog:~$ echo `date` && cat /proc/acpi/battery/BAT1/state 
Tue Jul 22 23:43:34 EDT 2008
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2819 mA
remaining capacity:      4197 mAh
present voltage:         11992 mV

```

This illustrates that that the values from my battery state are impossible.
At this point I decided to recompile my DSDT with iasl to see if was any errors. Lo and Behold the likely root of my issues:

```

zpowers@zilog:~/dsdt$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2792:                         Name (_T_0, Zero)
Error    4081 -             Use of reserved word ^  (_T_0)

dsdt.dsl  5317:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5331:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5346:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5361:             Acquire (MUTE, 0x0FFF)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5375:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5390:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5405:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 5646 lines, 174655 bytes, 2334 keywords
Compilation complete. 1 Errors, 7 Warnings, 0 Remarks, 38 Optimizations

```

When it comes to Fixing ASL errors, I am clueless. ASL is not a language I'm well versed in, so wadding through revesred ASL code is near impossible for me. I'm clueless on what to do next. I'm not even sure this DSDT is causing my issues.

Any clues on how to resolve this will be helpful.

---

### Post by sdennie on 2008-07-23
> **Milyardo said:**
> 
```

zpowers@zilog:~/dsdt$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2792:                         Name (_T_0, Zero)
Error    4081 -             Use of reserved word ^  (_T_0)

dsdt.dsl  5317:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5331:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5346:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5361:             Acquire (MUTE, 0x0FFF)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5375:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5390:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5405:             Acquire (MUTE, 0x03E8)
Warning  1103 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 5646 lines, 174655 bytes, 2334 keywords
Compilation complete. 1 Errors, 7 Warnings, 0 Remarks, 38 Optimizations

```


To fix the _T_0 error, I believe you can just replace all the occurrences of it in the code with something else (like foo0).  You may want to look at how it's scoped and make sure it's not being used outside the scope of the declaration before blindly changing all occurrences of _T_0 though.

As for the warnings, I'm not sure.  Looks like it's trying to get a mutex but, it's hard to know how you'd fix it without seeing it in context.  

At the very least, fixing the error will allow you to compile and see if it helps.

---

### Post by Milyardo on 2008-07-23
If it is a mutex then replace _T_0(it is a memory address or command?) with something else may not fix my issue at all since there may be some rouge function changing the value of my battery state.

---

### Post by sdennie on 2008-07-23
> **Milyardo said:**
> If it is a mutex then replace _T_0(it is a memory address or command?) with something else may not fix my issue at all since there may be some rouge function changing the value of my battery state.

Well, the _T_0 problem and the [possible] mutex problem are not related in this case.  The _T_0 problem is very common problem for BIOSes that have been compiled with the non standard Microsoft compiler.  Fixing that will at least let you compile and test.  It's impossible to say whether or not the new DSDT will fix your problem though.

---

### Post by slobapet on 2008-09-28
Hmmm, I got same reading. When running on AC and switching to battery power readings are fine but after a while it shows this:


sloba@sloba-laptop:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         **786 **mAh
last full capacity:      **49169** mAh
battery technology:      rechargeable
design voltage:          **1323** mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            MS-1637

serial number:

battery type:            LION

OEM info:                MSI Corp.

When on battery restarting doesn't helps, but shuting down and removing battery for running on AC fixes this bug

I'm running kubuntu 8.04 on MSI VR601
Maybe it's our vendor... I'm new to linux and don't know how to realy fix this little anoying error or bug. I foung somewhere that new kernel will fix this... but probably I will wait


This is real reading after plugin in AC and rebooting to battery 

sloba@sloba-laptop:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         **4800** mAh
last full capacity:      **4357** mAh
battery technology:      rechargeable
design voltage:          **11100** mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            MS-1637

---

