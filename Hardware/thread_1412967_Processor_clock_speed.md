---
title: "Processor clock speed?"
date: 2010-02-21
forum: Hardware
---

### Post by c4sper877 on 2010-02-21
Hi all, I have a real annoying problem:

I have recently bought a second hand Toshiba Satellite A60-106, with a Pentium 4, 3.06Ghz Processor...
For some reason kubuntu reckons that my processor is 1.862Ghz. :confused:

I used 'cat /proc/cpuinfo' and a system load viewer to check this and they both report the same speed.


At first I thought it was being under-clocked due to a previously installed memory module expansion (maybe running at the wrong FSB) but I removed the module and it still reports the same processor speed.

Any ideas would be greatly appreciated.:P
Thanks
#Lee

---

### Post by adam814 on 2010-02-21
It's a case of CPU Frequency Scaling.  For example mine is a Core 2 Duo 2.0 GHz and 'cat /proc/cpuinfo' reports the current CPU frequency (in this case 800 MHz).  The processor speed will increase under load, this is normal behavior.  This especially helps in laptops to save power.

---

### Post by c4sper877 on 2010-02-21
Hi adam814, thanks for your reply.


 hmmm, I did consider the power saving could've been the issue so I checked the BIOS and 'System Settings>Advanced>Power Management' in KDE and everything is set to maximum performance. So I tried putting the processor under a little load and re checked it. The result was that it still showed the same speed.

Are there any applications out there that can test this properly for me.

Thanks again
Lee

---

### Post by c4sper877 on 2010-02-21
I do, however, think you very well could be correct.:-k

---

### Post by adam814 on 2010-02-22
Well, if the speed isn't changing under load the CPU frequency governor is probably not what you want.  If it's set to "powersave" specifically your processor will be locked to the slowest speed.  I use "ondemand" with mine and it works fine.  I don't use KDE, but in GNOME there's an applet you can add to the panel to view and set it.  Or you could always do it on the command line with "cpufreq-selector".  I'm a bit rusty on the syntax, but the man page is pretty good.

---

