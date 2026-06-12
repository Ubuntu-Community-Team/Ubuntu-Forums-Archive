---
title: "Laptop getting hot in Kubuntu 6.06 - solutions?"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by albeano2004 on 2007-03-04
Hi there,
I installed Kubuntu 6.06 over Ubuntu 6.06 the other day, after being wowed by the beauty and power of the latest Knoppix disc that came across my desk. After much searching, and troubleshooting, I managed to get Adept working over my proxy, but my other problem has me stumped. I had a small applet in my taskbar in Ubuntu, which monitored the temperature. This usually started off at around 60-70 degrees Celcius, but quickly cooled back down to around 39-40 degrees, and went up to around 50 degrees max if watching a movie. However, according to the output of both acpi -t and acpitools, my average temperature (idle) on Kubuntu is around 70 degrees, going down to 65 with the fan on, then up to 70 again. 

How can I fix this problem? Is it a config file I have to edit? I know it's not a hardware problem, as like I said, Ubuntu had the laptop a lot cooler. I would really like to solve this problem, rather than having a melted blob of plastic instead of a laptop.

The vital specs:
Laptop model: IBM Thinkpad T30
CPU: Intel Pentium 4 M 1.9
Video Card:16mb ATI Radeon 7500 (with direct rendering on)


If any other information is needed to come to a solution, please let me know.

Your help is appreciated:)

---

### Post by floke on 2007-03-04
You might have processes running that are using up your CPU. Go to a terminal and use 'top' to see what's going on. I had a problem with beagled which kept blowing my fan. Removing beagle solved the problem.

---

### Post by albeano2004 on 2007-03-05
> You might have processes running that are using up your CPU. Go to a terminal and use 'top' to see what's going on. I had a problem with beagled which kept blowing my fan. Removing beagle solved the problem.
Hi,
Looks like this was the problem *fingers crossed* - the CPU temps are MUCH more stable and sensible now, more like under Ubuntu (if not better). I was really hoping to not have to go back to Ubuntu, as I like the K desktop much more!:) :) 

Thanks for your help!
albeano2004

---

### Post by floke on 2007-03-05
Glad it worked. Now the next step is to wean you off KDE :)

---

