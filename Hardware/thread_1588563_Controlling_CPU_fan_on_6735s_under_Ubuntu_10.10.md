---
title: "Controlling CPU fan on 6735s under Ubuntu 10.10"
date: 2010-10-05
forum: Hardware
---

### Post by gery4 on 2010-10-05
Hi. I have problem with CPU fan on my 6735s (Athlon X2, k10temp-pci-00c3). It is running very loud, but i can't lower it's speed.
I've tried to use pwmconfig but it says:
 /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed. I've also tried writing directly to /proc/acpi/thermal_zone/CPUZ/trip_points but it says: bash: echo: write error: Input/output error.
I know that it can run quietly, on the same workload on windows or in debian sqeeze fans had worked silent.
Any suggestions?

---

### Post by GoosFraaba on 2010-10-06
I have found the same problem with my HP 6540b i7. Nice and quiet with 64bit Lucid, then loud and constant after clean install with 64bit Maverick daily build from about a week ago. I have just left it in the hands of the Ubuntu Gods and trust it is fixed this Friday upon release.

---

### Post by GoosFraaba on 2010-10-14
Still not fixed after full Maverick release :(

---

### Post by GoosFraaba on 2010-10-14
I finally had success by installing the proprietary graphics driver for my  ATI card. I was trying to get by without installing it, but it fixed the  fan issue.

---

### Post by WinRiddance on 2010-12-11
I've had my HP 6735s for 18 months now and I too feel that Ubuntu 10.10 is a horrible drain on the system, even after using the ATI drivers. Neither Ubuntu 9.10 nor 10.04 had any problems (used the proprietary drivers then too). After I installed the latest Ubuntu 10.10, intentionally waiting 5 weeks for bugs to be ironed out, my system displayed numerous problems that I never had before ... the constantly screaming CPU just being one of them. I'm a power user and I do tons of graphic and photo work. After the past 18 months I've concluded (at least for myself) that the HP 6735s is pretty much a cheap piece of garbage that mostly looks nice. But since cheap is all that I can afford, cheap is what I get stuck with ... which also caused me to **switch back to Ubuntu 10.04** in recent days since it ran much smoother than the latest 10.10 version.

---

