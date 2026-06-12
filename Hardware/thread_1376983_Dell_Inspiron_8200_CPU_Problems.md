---
title: "Dell Inspiron 8200 CPU Problems"
date: 2010-01-09
forum: Hardware
---

### Post by MAJORdorMo on 2010-01-09
I have a Dell Inspiron 8200 with a 1.6 ghz Pentium 4. After about 5-15 minutes of using Ubuntu or Xubuntu for simple things (IM and web browsing), the fans on my laptop would go on full blast and everything would be extremely slow. According to the systems monitor, the processor would be at 100% usage a lot of the time. However, when I open up a terminal and run top, it never shows more than CPU 55% usage (even while the computer is horribly slow and the systems monitor shows 100% usage). The memory/swap usage is never a problem, just the CPU usage.

I have tried Ubuntu and Xubuntu 9.10, 9.04, 7.10, and even Damn Small Linux. Each distro had the same problems.

Also, up until about a month ago, I wasn't having any trouble at all with this laptop or Linux.

What could the cause of this be and how could I go about fixing it?

---

### Post by derekmbarnes on 2010-01-09
First, have you checked or been able to check the temperature of your processing unit? (Install acpi from Synaptic and run "acpi -t" in Terminal.)

Second, does the fan turn off after a few seconds and keep going off and on again, or does it just keep running?

---

### Post by MAJORdorMo on 2010-01-09
I ran the acpi -t command a few times, and even when the CPU usage is 100%, the temp ranges from 38 - 42 C. Not bad at all. Strange.

The fan doesn't go on and off, but starts up 5-15 minutes after the computer starts and never stops.

---

### Post by MAJORdorMo on 2010-01-10
Bump.

Nobody has any ideas on what could be wrong?

---

### Post by MAJORdorMo on 2010-01-10
I fixed it. In the BIOS, there was a setting that adjusted the CPU power when I didn't need it all. I changed it from Automatic to Best Performance and it works fine now.

---

