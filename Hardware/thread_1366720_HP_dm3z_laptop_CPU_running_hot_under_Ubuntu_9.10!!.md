---
title: "HP dm3z laptop CPU running hot under Ubuntu 9.10!!!"
date: 2009-12-28
forum: Hardware
---

### Post by xouhcoatl on 2009-12-28
I just got this laptop and installed Ubuntu 9.10. Everything works fine but the laptop CPU gets very hot, around 60c-66c on idle. While on Windows 7 it gets around 30c.

The specs of my laptop are:

AMD Turion Neo X2 Dual-Core L625 Processor (1.6GHz, 1MB) w/512MB
ATI Radeon HD 4330 Graphics 
4GB DDR2 System Memory (2 Dimm)
320GB 5400RPM SATA Hard Drive

---

### Post by xouhcoatl on 2009-12-30
I going to try if it runs hot with Ubuntu 9.04

---

### Post by viniosity on 2010-01-16
My guess is that it's a BIOS issue.. Here's [the thread]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/BIOS-broken-on-HP-Envy-15-and-DV6T-Quad/m-p/159958") for the HP Envy 13 & HP Envy 15.. probably the same problem affects this HP laptop too.. Shame because I'd consider buying it otherwise..

---

### Post by xouhcoatl on 2010-01-25
I don't think it is a BIOS issue cuz, the laptop doesn't run hot under Ubuntu 9.04.

---

### Post by xouhcoatl on 2010-01-31
I discovered why it is running hot!!

The ati driver cant be use so both of the graphic cards are on!!

The graphic cards are cusing all that heat!

---

### Post by derekmbarnes on 2010-01-31
Related thread for Toshiba Satellite: [http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161)

We've been trying to figure this problem out for 3 months with no headway. Could you kindly elaborate on how you figured out the ATI graphics card was causing the problem, and whether you know how to fix it?

---

### Post by xouhcoatl on 2010-02-01
There is no fix yet? 
I don't know if this is related to your laptop.
here is the bug filed for the dm3z
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/486714](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/486714)

This laptop has switchable graphic cards an it is not able to use fglrx dirver.

fglrx driver has powermanegment.

It only works with the open source ATI drivers but they don't have power manegment.

Both graphic cards are turned on, making a lot of heat and wasting power.

---

### Post by illuminatifire on 2010-02-12
> **xouhcoatl said:**
> I don't think it is a BIOS issue cuz, the laptop doesn't run hot under Ubuntu 9.04.

Is this true? I'm thinking of getting a dm3z cause of the sweet price tag, but don't like the issue with the video card.  Why just 9.10? I thought the problem was their being no support for switchable graphics card.  I would most likely be getting ATI Radeon HD 3200 Graphics card. There also seem to be [proprietary drivers from ATI]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=us&rev=10.1&ostype=Linux%20x86") that were recently release but I think they only address the problem with the 4300 series. I have no way of testing since I don't have one yet, but I'd like to get one once a lot of the driver issues are worked out. Any opinions?

Also what version of fglrx, the kernel and ATI drivers are you running? [There seems to be something related to the kernel and vesion of fglrx and also being able to disable the switchable option?]("http://www.thinkwiki.org/wiki/Problems_with_fglrx#X_server_gives_an_error_.22Invalid_video_BIOS_signature.22_after_installing_fglrx")

---

### Post by 9tails on 2010-07-23
I have a similar problem with an HP DV3 (dual graphics card) and other laptops. The culprit seems to be the infamous nohz balance code in the kernel, causing a crazy amount of load balancing tick wakeups (you can verify installing powertop). Luckily the issue is going to be fixed in kernel 2.6.35. See [http://ubuntuforums.org/showthread.php?p=9600503#post9600503](http://ubuntuforums.org/showthread.php?p=9600503#post9600503)

---

