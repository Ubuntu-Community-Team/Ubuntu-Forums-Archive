---
title: "Poor Performance"
date: 2008-11-16
forum: Hardware
---

### Post by apollyon0810 on 2008-11-16
I have a laptop I would very much like to use Linux on for my day-to-day.  It is a Toshiba Satellite A215-S7472.  Specs:

AMD Turion 64 X2 2.2Ghz
2 GB DDR2 RAM
250GB HDD
Mobility Radeon HD2400 64mb dedicated, up to 255 mb shared.

I really don't have any GLARING issues with my installation.  I just suffer from poor performance.  Ibex x64 installs without a hitch, and the restricted drivers manager installs fglrx fine.  Compiz-Fusion loads without error and gives me all the eye-candy I want.  But the OS is slow slow slow...  slow response times, especially when switching between tabs in Firefox.

I really want to use Linux, but as far as performance goes, Vista blows Ubuntu out of the water.  Please tell me that I'm doing something wrong and that I'm not just stuck.

---

### Post by Therion on 2008-11-16
Humor me and try using Ubuntu 8.04 (Hardy Heron) instead.

---

### Post by apollyon0810 on 2008-11-16
> **Therion said:**
> Humor me and try using Ubuntu 8.04 (Hardy Heron) instead.

I had the same issue with Hardy Heron.  :(

---

### Post by malfist on 2008-11-16
Perhaps install htop and watch what uses the most cpu when switching tabs, and let us know...

---

### Post by apollyon0810 on 2008-11-16
> **malfist said:**
> Perhaps install htop and watch what uses the most cpu when switching tabs, and let us know...

Firefox was just an example.  This happens with all programs and windows.  Just an overall laggy system.

---

### Post by malfist on 2008-11-16
Yes, but it could be something with Xorg, or possibly one core is turned off, or everything is throttled. Let us know.

---

### Post by apollyon0810 on 2008-11-16
> **malfist said:**
> Yes, but it could be something with Xorg, or possibly one core is turned off, or everything is throttled. Let us know.

I installed htop.  Not really sure exactly what I'm looking at, but I can say that both cores are working.  The cores won't both "max out" at the same time.  Either both at 50%, or one or the other at 100% when quickly cycling through the tabs.  Normal usage on both when just idling.

---

### Post by CholericKoala on 2008-11-16
> **apollyon0810 said:**
> I installed htop.  Not really sure exactly what I'm looking at, but I can say that both cores are working.  The cores won't both "max out" at the same time.  Either both at 50%, or one or the other at 100% when quickly cycling through the tabs.  Normal usage on both when just idling.

If you can, you can go into your bios and make the core FSB static so that it wont change/throttle.

RMClock is a software solution for windows that can make your FSB static.  I dunno what it would be for linux, but thats what you need to do.  Good luck. :popcorn:

---

### Post by bobnutfield on 2008-11-16
I cannot tell if there is anything wrong with your install from what you have posted, but my laptop is the same model and spec.  I am running Intrepid 8.10 32bit and the system is fast and smooth.  I did have some sluggishness with the live 64bit cd, but I just attributed that to running from the cd.  In any case, I have always a happier system running 32bit Ubuntus.

---

### Post by apollyon0810 on 2008-11-16
> **bobnutfield said:**
> I cannot tell if there is anything wrong with your install from what you have posted, but my laptop is the same model and spec.  I am running Intrepid 8.10 32bit and the system is fast and smooth.  I did have some sluggishness with the live 64bit cd, but I just attributed that to running from the cd.  In any case, I have always a happier system running 32bit Ubuntus.

Did you have to do anything special while installing the ATI driver?  I AM running the 64 bit version.  I have a 32-bit version burned, but it kept freezing when I tried to install it.  64 bit version didn't complain.

---

### Post by bobnutfield on 2008-11-17
> **apollyon0810 said:**
> Did you have to do anything special while installing the ATI driver?  I AM running the 64 bit version.  I have a 32-bit version burned, but it kept freezing when I tried to install it.  64 bit version didn't complain.

No, I simply enabled it from the System>Administration>Hardware Drivers.  I started with this installation while Intrepid was in Alpha 5 and followed the updates through to its release.  I have never had good luck with a 64bit distro on my laptop, though I have successfully run 64bit Fedora on my AMD64 desktop.  Even if I were to install it with no issues, there is only very minimal performance improvements.  The only reason I can think of when you MUST use 64bit is when you have 4GB or grreater of memeory as the 32bit will only utilize 3GB.

---

### Post by EV500B on 2008-11-17
Could it be an bios misconfiguration, like the laptops' "Low mode" which decrease its energy consomation and performance. Or something like that?

---

