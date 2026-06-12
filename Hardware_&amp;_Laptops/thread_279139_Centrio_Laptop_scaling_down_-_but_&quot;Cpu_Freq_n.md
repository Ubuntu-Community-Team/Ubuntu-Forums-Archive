---
title: "Centrio Laptop scaling down - but &quot;Cpu Freq not supported&quot;"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by ikonia on 2006-10-17
I am using an MSI S260 laptop with a fully updated ubuntu 6 install

My Cpu is a Centrino unit as shown bellow

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 798.371
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1598.60


As you can see its a 1.6ghz cpu - thats currenty running at 789 mhz.

The lapotp is plugged in and the cpu should be running at full power.
This is backed up by the gome desktop applet that shows its being run at 798.

If I try to get the CPU frequency from cpufrequtils I get the following

cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU


So if no frequeny driver is active ? whats scaling it down ?
Why would a scalable centrino CPU not be shows as scalabe ?

I am open to suggestions.

Many thanks

---

### Post by ikonia on 2006-10-20
can't believe I didn't get any response to this.

I'll give it a bump to see if anyone has any fresh opinions.

---

### Post by ikonia on 2006-10-21
here is a screeen shot of my destkop - pay attention to the cpu frequency on the task menu bar - and the message

If scaling is not supported - then was is it being scaled down.



[[IMG]http://img205.imageshack.us/img205/8190/screenshotjj8.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotjj8.png)"][[IMG]http://img205.imageshack.us/img205/8190/screenshotjj8.th.png[/IMG]](http://img205.imageshack.us/my.php?image=screenshotjj8.png)

---

### Post by karthikp on 2006-10-21
[This link]("http://ubuntuforums.org/showthread.php?t=45452") might be useful. It's about a KDE app called klaptop, but there's a good discussion of the power profiles. So, if you want your CPU to run at its full speed, set the power profile to performance...

---

