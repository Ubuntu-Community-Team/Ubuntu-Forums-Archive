---
title: "Frequency scaling crashes on Sempron"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by Yohumbus on 2006-01-15
Ok... I have a laptop that is using a Sempron 2800+ that I would really like to get frequency scaling working. Note that my laptop and processor does have the clock timer bug that quadruples my timer (I fixed this with disable_timer_pin_1 in the kernel options as found in these forums). 

Ive looked through dmesg and found that while booting, ACPI reports that there are 8 frequencies to choose from, but when I try to choose from one of these in the KDE power management menus the system hangs. Also in dmesg when the scaling module starts (forgot the name.. its *_K8 though) the module says that there are 2 scaling modes to choose from.

I have tried using powernowd and it will run without the system hanging but I never see the clock speed change. I tried installing cpudyn but it only caused my system to hang at boot (presumably from using the ACPI states).

At this point I don't know what to try to get this working... my only other guess is that I need to disable the ACPI scaling to force programs to use the native (*_K8 ) module for scaling. I use gentoo on my desktop so I am familier with linux but I wouldn't know how to do this in kubuntu. If anyone could help me with this or have any other suggestions they would be appreciated.

---

### Post by Yohumbus on 2006-01-15
alright... I fixed it.. I dont have much time right now but I will say what I did to fix it later..

---

