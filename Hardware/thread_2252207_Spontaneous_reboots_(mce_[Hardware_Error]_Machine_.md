---
title: "Spontaneous reboots (mce: [Hardware Error]: Machine check events logged)"
date: 2014-11-10
forum: Hardware
---

### Post by Lólindir on 2014-11-10
Hi all,

I have since a while a new desktop system, based on an Intel 4790K and a Gigabyte GA-Z97X-UD3H motherboard. As a lot of people I am dealing with quite high temperatures, reaching 70°C - 80°C under load, with Prime95 small FFT's even 100°C. According to Intel, this shouldn't be a problem.

Since a couple of days I am often using Handbreak to encode some movies. This is causing a processor workload from 90% - 100%. Everything seems to run fine, but after 1h - 2h I'm often getting a spontaneous reboot. I had a look in the system log yesterday evening, and I found this entry

```
Nov  9 19:12:16 yoda kernel: [  136.893167] init: plymouth-stop pre-start process (1871) terminated with status 1
Nov  9 19:14:59 yoda kernel: [  299.821999] mce: [Hardware Error]: Machine check events logged
```

Next I have installed mcelog and I found this back in the log:

```
mcelog: failed to prefill DIMM database from DMI data
Hardware event. This is not a software error.
MCE 0
CPU 3 BANK 1
MISC 86 ADDR 1424bd400
TIME 1415556598 Sun Nov  9 19:09:58 2014
MCG status:
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
SRAR
MCA: Data CACHE Level-0 Write Error
STATUS bf80000000000124 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0
CPUID Vendor Intel Family 6 Model 60
```

I am not a Linux expert, so some help to find out what is going wrong would be nice :)

I suspect a processor issue (heating?).
I don't think it is a RAM issue as I was some time ago running Memtest86+ for 1 or 2 hours without finding any problem.

Some more system info:
I am using Ubuntu 14.04 with the latest Nvidia drivers from the xorg-edgers repository (I have a 750 Ti card).
I'm having 16GB RAM and have mounted /tmp as a RAM drive.
If you need more system info, please let me know.

Many thanks for your help!

---

### Post by houstonbofh on 2014-11-10
The CPU may be able to handle the heat, but what about the graphics card, memory and chipset?  Try opening the case and blowing a fan on it while you handbrake overnight.  If it survives, you know heat is the problem.

---

### Post by Lólindir on 2014-11-11
Hi,

I was yesterday running a Handbreak job for about 2 hours, this time without reboot. I was constantly monitoring the temperatures with psensor, and besides the cpu temperatures the other temperatures looks fine to me: gpu is constantly below 30°C, chipset as well. I will have a more detailed look tonight and post some temperatures for all sensors.

I also had a look at the cpu (core) temperature threshold values, and noticed that 80°C is the threshold value for 'high', while 100°C is the threshold value for 'critical'. As far as I can see the core temperatures remain below 80°C when running Handbreak. Temperatures seems to go till 75°C but not higher, remaining most of the time around 69°C. But it might be that sometimes there is a small spike to 80°C. What happens when a cpu core hits the threshold value for 'high' (in this case 80°C)? Will this result in a reboot / shutdown or will nothing happen until the critical value is reached?

Are there other things I can/should monitor when testing?
Would it be useful to upgrade to 14.10 before further testing?

---

### Post by Lólindir on 2014-11-12
As promised some more feedback.
The other temperatures seems to be OK as far as I can see (temperatures read with psensor). Only the cpu sensors are showing the high temperatures (which is, regarding Intel, normal).

I've run memtest86+ during the night for more than 8 hours. I didn't get a single memory error reported by memtest86+, so I think I can exclude the (RAM) memory as a potential problem. Anyone a suggestion how to proceed further?
I was thinking to stress test the machine while logging the temperatures (anyone a suggestion which tool to use?), or to convert some movies with Handbrake during the night for a couple of hours while logging the temperatures.

Many thanks for your help!

---

### Post by houstonbofh on 2014-11-12
If handbrake is what is causing the reboots, handbrake is the best stress test.

---

### Post by Lólindir on 2014-11-12
OK, I have stressed my pc again with Handbrake and I could reproduce the issue. The reboot happened when I was in the meantime surfing on the web, after more than 1 hour of video encoding. At a certain moment the pc freezed completely, and approx. 1 minute later there was a reboot.
I cannot find anything back in the system log, but when running mcelog and watching the generated log file I have exactely the same error message:

> mcelog: failed to prefill DIMM database from DMI data
Hardware event. This is not a software error.
MCE 0
CPU 3 BANK 1 
MISC 86 ADDR 171c838c0 
TIME 1415833222 Thu Nov 13 00:00:22 2014
MCG status:
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
SRAR
MCA: Data CACHE Level-0 Write Error
STATUS bf80000000000124 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 60

The processor load was around 90%-95%, the cpu temperature around 75°C (a bit less, however I'm not sure of the exact temperature when my computer was actually freezing as also psensor was freezing).
Since 100°C is marked as critical, I'm not sure if it could be a temperature issue as it is still 25°C less than the critical threshold.

How can I find out what is exactly causing the problem? Right now I can only tell that my RAM memory seems to be OK and that the problem is reproducible with Handbrake...

Thanks for helping!

---

### Post by Lólindir on 2014-11-14
Unfortunately no responses anymore...

Anyway, I had contact with Intel support in the meantime and they will send me a replacement cpu in order to test if the issue is processor related or not. I've also contacted Gigabyte support in case the issue would not be solved with a new cpu. Fingers crossed...

Are these kind of errors 100% because of hardware malfunction, or can it also be a kernel or software problem?

---

### Post by houstonbofh on 2014-11-16
I would test it again with the case open and a room fan blowing at it to eliminate heat as the issue.  If it is still one hour in, you know it is not heat.  If it now goes 4 hours, you know it is.

---

