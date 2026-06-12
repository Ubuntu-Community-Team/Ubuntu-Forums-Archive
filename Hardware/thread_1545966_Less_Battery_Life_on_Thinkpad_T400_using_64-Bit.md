---
title: "Less Battery Life on Thinkpad T400 using 64-Bit?"
date: 2010-08-04
forum: Hardware
---

### Post by nbotticelli on 2010-08-04
I recently purchased a New-In-Box Lenovo Thinkpad T400 laptop which I have just loaded Ubuntu 10.04 64-bit onto.

I have a six cell and a nine cell battery but it seems that battery life is much less than when I have run 32-bit Ubuntu on another T400 that a friend has. 

I don't have hard data yet but battery life does seem to be quite lower than it should be and I am just wondering if 64-bit Ubuntu in general might use more juice than 32-bit would.

I'll post more "hard" data once I have done some testing but for now I am just wondering if anyone else has experienced anything like this before.

The specs:
Lenovo Thinkpad T400
Switchable graphics: ATI Mobility Radeon HD 3470 or Intel GMA 4500MHD
CPU: Intel Core 2 Duo P8600 @ 2.40GHz TDP-25W
4GB RAM
160GB 7,200 RPM HD
14-inch screen @ 1440x900 resolution
Intel 5100 wifi card and bluetooth chip.

Thank you!

---

### Post by corrytonapple on 2010-08-04
No, wouldn't think so. Is your friends laptop older?

---

### Post by wirawan0 on 2010-09-07
I don't think so either. 

BTW this is my stats for extreme battery savings: I used to run Ubuntu 8.10 and the power usage could not go down from 11 watts minimum on battery (no wireless etc). I am now running 64-bit Sabayon Linux with kernel 2.6.31, and I could get the battery usage down to 8.5 watt (with dim enough screen and no wireless and no stray background process such as firefox). I am disabling the discrete graphics and using Intel integrated exclusively for now. I would think 10.04 does at least as good as this.CMIIW.

But maybe your hardware config matters. I have 2 GB RAM with no bluetooth or built-in card reader. I disabled the ATI discrete graphics via BIOS.

BTW the instantaneous battery usage can be seen from file /proc/acpi/battery/BAT0/state  (cat it, it's a text pseudo-file).

Wirawan

---

### Post by aezren on 2010-10-28
I just found your post and thought I would give you my 2 cents. I have a Lenovo T400 with the 6 cell battery. With Windows 7 32bit i would get about 4.5 hours on a charge of casual internet browsing. With the past few versions of Ubuntu 32bit (including 10.10) i would only get about 2.5 hours out of my battery. I finally found a post where a guy had better times with the 64 bit version. I installed 10.10 64 bit and now am getting 4.5 hours out of the box with no power tweaks at all. 64 bit made a big difference for the better for me. I am not sure why your run times have actually gone down with 64bit. Have you actually tried putting 32 bit on your laptop to see if there is a difference?

---

