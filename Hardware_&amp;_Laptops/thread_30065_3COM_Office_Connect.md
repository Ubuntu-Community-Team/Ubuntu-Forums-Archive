---
title: "3COM Office Connect"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by cucaracha on 2005-04-27
I installed the 3COM Office Connect wireless card on my computer yesterday. As I found a bug in the process, I am gonna document it here in case someone hits the same problem.

I needed ndiswrapper, so I downloaded the ndiswrapper-source and ndiswrapper-tools packages. Then I went to download kernel-source-* but I couldn't find the package. After much searching I realised that the kernel packages are now called linux-source linux-kernel-headers and so on, so I installed the linux-kernel-headers-* matching my kernel.

Once I compiled it, I made the package with the debian/rules script and installed it. Then I configured the card (ndiswrapper -i 3c*.inf on the folder that contained the windows drivers).

When I tried to load the driver (modprobe ndiswrapper) it gave me an error message about invalid option "|". After much googling I could not find the solution, so I decided to have a look  at the file that gave the error (you can get the error from /var/log/syslog) and I found a line with just "|" in it. I deleted that line and now everything works.

Is this a bug in ndiswrapper? A bug in the .inf file? Anyway, hope someone finds this useful.

---

