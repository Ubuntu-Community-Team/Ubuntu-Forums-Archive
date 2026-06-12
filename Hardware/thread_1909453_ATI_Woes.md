---
title: "ATI Woes"
date: 2012-01-15
forum: Hardware
---

### Post by -=WaLrUs=- on 2012-01-15
Hello,

  I have just updated from an old version of ubuntu to the 11.10 which I have jsut insalled on a Shuttle (SN45G V3).

Anyway the mobo came with a Radeon 9600 (I'm in the process of getting an Nvidia card).  But I thought that I would install the ATI whilst waiting. 

I've gone through various methods, installed the catalyst  driver and can see it as one of the apps I've installed.  I tried to run catalyst and get the following error :

[I]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/I]

If i try and run aticonfig via terminal I get the response:

*no supported adapters detected!*

I've also checked to see and from lspci I can seen the card is detected, so it looks like driver issue (install?).

Would a kind sole please be able to point me in the right direction!

Many thanks!

---

### Post by coffeecat on 2012-01-15
You're out of luck with that old ATI graphics chipset and recent versions of Ubuntu. AMD have designated it a legacy device and no longer support it with their proprietary catalyst driver.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

The only driver that will work with it in 11.10 is the default open source one.

---

### Post by -=WaLrUs=- on 2012-01-15
Thanks for the response.

If the Nvidia I grab is listed as legacy, then I can use that card with the legacy driver rather than their latest driver.

(It looks like I may have a gefroce4 being donated to me) 

The geforce4 series are now classed as legacy, hence the question.

Just to clarify, I don't need blistering 3d just a couple of design progs I use need 3d, so hopefully the geforce4 will work!

Many thanks!

---

