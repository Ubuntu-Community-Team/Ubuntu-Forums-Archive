---
title: "CPU heating"
date: 2010-12-04
forum: Hardware
---

### Post by slayer69sk on 2010-12-04
Hello

I have Notebook Acer aspire timelineX 5820TG with Intel(R) Core(TM) i5 CPU M 460  @ 2.53GHz, and have too high temperature. I put my processor to lower frequency (1.2GHz) and temp monitor show 52 but im not sure because its too hot for touch. Im using cpufrequtils. Anyone can help?? In windows is temp 25+-.

for example:

zuzanka@zuzanka-laptop:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
stepping	: 5
cpu MHz		: 1199.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5053.80
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

powermanagment is missing its normal??
Thank you

---

### Post by Kixtosh on 2010-12-04
If your temperature is showing 52°C, I'm not convinced you have a problem. All of my laptops run hotter than that, including one that idles frequently at 60°C, and rises to 75°C during video activity such as YouTube. 

I wouldn't worry unless the fan is not activating and speeding up as the temperature rises. You are probably well within the CPU limits (these are frequently as high as 90-105°C, although I would usually aim to keep 15° to 20° below those limits).

The sensor measurements are not very accurate, but you should note that many laptop cases will get quite hot, especially on the underside, during normal operating conditions. This is most obvious for smaller "ultra-portable" laptops. I would only worry if the fan isn't coming on at all at temperatures exceeding something like 65°C, and in that regard, I would also mention that Windows seems to trigger fan operation far more frequently than Ubuntu in general on my laptops.

---

### Post by slayer69sk on 2010-12-04
I have another laptop with procesor intel Q9000 with scaling 1.6Ghz-2Ghz (its quadcore too), i5 is 35W but Q9000 is 45W monster!! Im using 1.6Ghz and its too much cooler.

I dont trust to this sensor because when i have heat on my second laptop with Q9000 like with i5, the sensors showing over 75C. And i must turn on lot of aplications to make this heat. Dont tell me the that procesor with better scaling (1.1GHz-2.8GHz) and with lower power consumption is producing more heat on whole desktop without running aplications.
 
And when i compare it in windows the result is so much different. Q9000 - 50C and 2 hours on batery. i5 - 25C and 6hours on battery. I know about linux that he havent best power saving and notebooks havent best timeline on battery, but my CPU is real hot and its not normal. 

I think somewhere is mistake.. maybe it showing scalling but it dont scale.. because it has default turned on maximal freq, and when i changed it, the temp from fun doesnt changed. 

Thanks in advanced

---

### Post by Kixtosh on 2010-12-06
Well, checking your results in your first post, compared to mine, they are just about identical (except for the values, because we don't have the same CPU), so the fact that the "Power Management" line is blank doesn't seem to be anything to worry about. 

As for the rest, you are convinced it is running too hot and not scaling, but I'm not sure why exactly. Does the fan run at all? Does the fan seem to run as fast as in Windows when the temperature rises to 75°C?

What you could also do easily is install the CPU Frequency Scaling Monitor applet in the top panel (just use a right click and select "Add to Panel", then choose the Monitor from the list of available items). This would enable you to:

1) See if the frequency is indeed changing during use.
2) See if manually forcing a lower CPU frequency lowers the temperature.

---

### Post by LinuxCharms on 2010-12-06
If you're concerned you have a problem, you could always buy a cooling pad.

Any pad is sufficient, I personally like this one:
[http://www.amazon.com/Performance-Aluminim-Cooling-Toshiba-Satellite/dp/B00126RZR2/ref=sr_1_24?s=pc&ie=UTF8&qid=1291655015&sr=1-24](http://www.amazon.com/Performance-Aluminim-Cooling-Toshiba-Satellite/dp/B00126RZR2/ref=sr_1_24?s=pc&ie=UTF8&qid=1291655015&sr=1-24)

---

### Post by mikejjp on 2011-08-16
Acer 5315. I got rid of the rubbish Visa O/S that the laptop came with. Then discovered that CPU temperature control was needed, and didn't come with Ubuntu or Mint. It's taken a while to get the machine to stop cutting-out when the CPU overheats - by having a fan blow cool air into the bottom of the unit.  But now at last I have enough time to install a new BIOS and software to do temperature control, and yes, the Linux O/S.

---

### Post by Kixtosh on 2011-08-17
> **mikejjp said:**
> Acer 5315. ...  But now at last I have enough time to install a new BIOS and software to do temperature control, and yes, the Linux O/S.Please post back with what you did and how you did it, in case it helps others. Good luck with your endeavor!

---

