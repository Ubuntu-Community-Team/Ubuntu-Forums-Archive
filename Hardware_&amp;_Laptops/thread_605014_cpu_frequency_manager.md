---
title: "cpu frequency manager"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by jad2753 on 2007-11-06
OK! I took the plunge and installed 7.10 on my laptop, a Twinhead 
R15B Durabook. It has the Pentium M 1.6 proc running at 600 mhz
I added the CPU Frequency Scaling Monitor applet to my bar and gives
me a message that scaling is unsupported. It would be nice if I could
coax full speed from this processor as DVD's play with a frame every
second or so. What is my next step?

---

### Post by henklaak on 2007-11-06
I had a similar problem and "sudo modprobe acpi-cpufreq" solved it...
I vagely recall that I had to install it through Synaptic first.

Please see if it works and get back if it doesn't: I will look into it in more detail.

Regards,
Henk.

Or you might look at this (rather old and no longer completely accurate) thread:

[http://ubuntuforums.org/showthread.php?t=248867]("http://ubuntuforums.org/showthread.php?t=248867")

---

