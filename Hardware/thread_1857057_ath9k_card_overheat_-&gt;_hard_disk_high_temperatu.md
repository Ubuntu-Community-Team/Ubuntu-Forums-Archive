---
title: "ath9k card overheat -&gt; hard disk high temperatures on HP DV5"
date: 2011-10-09
forum: Hardware
---

### Post by blackshard on 2011-10-09
Hi all,

I'll explain what I discovered. I'm using ubuntu 11.04 with all updates in place.
I own an old HP dv5 laptop with AMD configuration. This information is crucial because dv5 models mount their wireless card very close to the hard drive.
My hard drive is Western Digital, well known for the reload cycling count issue. The wireless card is a azurewave card with atheros AR9285 chip and using the ath9k module.

When I installed ubuntu 11.04, I noticed very high temperatures for my hard drive, up to 55-56°C. 
I noticed that ubuntu disables my hard drive power management, and promptly restored it with this command:

> hdparm -B 128 /dev/sda

then the temperatures lowered during idle periods, but during high usage periods I reached 52-53°C and even more.

That was disappointing, so I started doing some tests on both Windows 7 and ubuntu, with and without the wireless card installed.

With the card installed I have this:

in Windows 7, the idle temperature of the disk is 42°C
In Ubuntu 11.04, the idle temperature of the disk is 48°C

With the card uninstalled I have this:

in Windows 7, the idle temperature of the disk is 41°C
in Ubuntu 11.04, the idle temperature of the disk is 42°C

So, most probably, the card is overheating the hard drive in my particular configuration.
I tried to disable the network, remove the ath9k module and enable power management via iwconfig wlan0 power on and iwconfig wlan0 power timeout 500ms but had no success, the hard drive temperature always rises.

Any guess?

---

### Post by coffeecat on 2011-10-09
FTR - prior to soft-deleting. Duplicate here:

[http://ubuntuforums.org/showthread.php?t=1857046](http://ubuntuforums.org/showthread.php?t=1857046)

---

