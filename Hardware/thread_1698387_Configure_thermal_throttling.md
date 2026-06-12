---
title: "Configure thermal throttling"
date: 2011-03-02
forum: Hardware
---

### Post by Zendoin on 2011-03-02
Hi :)

I'm running Ubuntu 10.04 on a machine with an ASRock 775Twins-HDTV motherboard and an Intel Pentium D CPU. When my cpu gets too hot (above 70°C I think, not too sure) I get these messages in my /var/log/syslog:
"Core temperature above threshold, cpu clock throttled" and
"Core temperature/speed normal" some seconds later.
The problem is: the more often this happens, the slower my machine gets, for whatever reason... So I tried to avoid this by disabling any thermal throttling (for CPU and for mobo) in the bios settings. Gave no change. Installed mcelog, when I run "sudo mcelog" I get more information:

```
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 0
CPU 1 THERMAL EVENT TSC 2857ef4e902 
TIME 1299066376 Wed Mar  2 12:46:16 2011
Processor 1 heated above trip temperature. Throttling enabled.
Please check your system cooling. Performance will be impacted
STATUS 3 MCGSTATUS 0
MCGCAP 180204 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 15 Model 4
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 1
CPU 1 THERMAL EVENT TSC 2857f301a54 
TIME 1299066376 Wed Mar  2 12:46:16 2011
Processor 1 below trip temperature. Throttling disabled
STATUS 2 MCGSTATUS 0
MCGCAP 180204 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 15 Model 4
```

The problem is no longer that relevant since I cleaned my cpu cooler and built in a better fan so that my machine nearly never reaches critical temperatures. But it still puzzles me... So:

- Why is it continiously getting slower each time it throttles and gets back to normal speed?

- How can I disable thermal throttling if not in bios??? At least I'd like to manually set the threshold temperature...

Any HW specialists out there that could help me with this?

---

### Post by Zendoin on 2011-03-03
Hmmmm, no ideas? :confused:

---

### Post by Zendoin on 2011-03-05
Is this not the right place to ask or did I get anything else wrong? :(

---

