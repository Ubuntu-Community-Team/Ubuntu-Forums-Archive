---
title: "2 Problems, Dual Threading (NOT) &amp; Does not power down"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by carlc on 2005-01-29
I am new to Ubuntu and have a clean install, about two days old. I have two issues which I guess are related to the kernel that I am using and my motherboard.

I have an elitegroup PT800CE-A motherboard which supports hyper-threading, as does my P4 cpu. My resource monitor currently only shows one cpu being used. Also, when I shutdown my pc, everything seems to shutdown properly. However, my pc does not turn off even after receiving the power down signal.
 :confused:   
Any ideas and help on these issues would be greatly appreciated.

---

### Post by tragek on 2005-01-30
[QUOTE=carlc]I am new to Ubuntu and have a clean install, about two days old. I have two issues which I guess are related to the kernel that I am using and my motherboard.

I have an elitegroup PT800CE-A motherboard which supports hyper-threading, as does my P4 cpu. My resource monitor currently only shows one cpu being used. Also, when I shutdown my pc, everything seems to shutdown properly. However, my pc does not turn off even after receiving the power down signal.
 :confused:   
Any ideas and help on these issues would be greatly appreciated.[/QUOTE]
 In order to use 'both' HT cpus, one must be running an smp kernel. Install the i686-smp kernel image.

---

### Post by Yoda_Oz on 2005-01-30
i managed to successfully upgrade to an smp kernel but i had to revert back to the 1 cpu kernel because i kept having problems with my wireless pcmcia card.
maybe someone has the same problem?
what happens is that the internet works for about 10 seconds and the it freezes. i have to restart the eth1 interface to be able to start browsing again... for 10 secs...
there must be something in the kernel that makes the pcmcia wireless card power down or timeout or something else. im using the yenta-socket module for pcmcia and atmel module for my pcmcia wireless card...
as soon as i reverted back to the original 'hoary' kernel it worked fine again.

somebody let me know if you've had the same problem.

---

### Post by carlc on 2005-01-30
How do I install the i686-smp kernel image?

---

### Post by Sham on 2005-01-31
[QUOTE=carlc]How do I install the i686-smp kernel image?[/QUOTE]

sudo apt-get install linux-686-smp

take a look at:

[http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

---

### Post by carlc on 2005-02-01
Thanks!

---

