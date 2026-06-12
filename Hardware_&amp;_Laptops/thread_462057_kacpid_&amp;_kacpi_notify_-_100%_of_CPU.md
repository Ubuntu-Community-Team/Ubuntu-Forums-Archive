---
title: "kacpid &amp; kacpi_notify - 100% of CPU"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by FuriousLettuce on 2007-06-02
I have been having troubles with CPU usage spikes. The culprits are kacpid and kacpi_notify. It generally tends to occur when I myself am running a CPU intensive process. Neither kacpid or kacpi_notify are killable, even as root, so the only way that I've found to counteract this is to hibernate / shutdown / restart - which takes about 5 minutes due to the intensive CPU usage. I've searched around, and other people do have this problem, but the general solution seems to be to simply switch acpi off. However, as this is a laptop, and I use the acpi features all the time, that's not an option. I wondered if anybody might have any ideas, as it's driving me mad.

I'm running Feisty on an HP nc4200 (1.86Ghz Pentium M, Centrino (ipw2200) wireless, 512MB RAM.

---

### Post by copperhead on 2007-06-02
I'm having the same problem, only they're not spikes.  My kapcid process is constantly sitting at 90-92%.

---

### Post by ethaniscool on 2007-06-06
I too am having this problem even while typing this. If someone could instruct me on how-to turn acpi off it would be greatly appreciated.

---

### Post by suyashjain on 2007-06-10
The thing is indeed a kernel-daemon process, it handles
power-saving functionality and a few other things that are
specific to ACPI compliant motherboards (like monitoring
temperatures, rpm's of fans, ... ) ...

You probably don't need it on your machine, if it hogs
99% CPU something is definitely wrong with your machine,
either with FUDora's set-up, or with your BIOS' ACPI
implementation... 

Kindly deactivate the services , if you don't want to monitor the temperature or use the latest kernel version.

My Personal suggestion is to stop the service itself.

---

