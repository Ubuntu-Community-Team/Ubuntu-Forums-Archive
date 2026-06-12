---
title: "Thinkpad T30 and ACPI"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by thepoch on 2005-04-12
Hi folks,

I'm wondering, has anybody ever encountered the fan not starting up, while the CPU staying at the highest speed (even when not doing anything)?

I just noticed that my T30's fan didn't start, while staying at 1.8ghz. It reached a temperature of 86 degrees Celcius! I only noticed when I smelled something like burning metal. It didn't shutdown though or slowdown though, so I just powered it off, and stuck it in front of a fan and air conditioner for a few minutes.

Anything to watch out for? I noticed that in my /proc/acpi/thermal_zone/THM0/trip_points, passive temp is at 87C, and critical is at 94C. Sounds a little too high for me. Anyway to set this up to a more acceptable level at startup (or is echo blahblah > /...../trip_points my only option?)?

And as far as I read about laptop_mode, it's just for throttling harddrive usage. Is this correct? Or does it affect bigger things than that?

And any way to set that the fan starts up as long as it reaches 50C, whether or not I'm on batteries?

I'm taking notes of my installation of Hoary this time, so any help would be great as I'll post as much info as I can about Hoary and my T30 online when I finish up and get some free time.

Thanks!

---

### Post by hil on 2005-11-18
This is my output:

/proc/acpi/thermal_zone/THM0/trip_points
critical (S5):           87 C
passive:                 79 C: tc1=5 tc2=3 tsp=600 devices=0xc14d5560

I don't have the environment to test my T30 in high temperature. How do I know if my fan should start? My CPU usage is not always 100%. You probably had some processes that occupied CPU resources. run top on the command line to check.

---

