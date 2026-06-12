---
title: "Power conservation notes"
date: 2010-05-02
forum: Hardware
---

### Post by lavinog on 2010-05-02
I have been running 10.04 on my laptop for a couple of months, and one of the things I have noticed was that my battery only lasts about an hour now.
UPDATE:  I think I have determined that the battery is just old.
One thing I suspected was the open source radeon driver.  The driver has some power saving features, but they can only be enabled with a 2.6.34 kernel (Lucid uses a 2.6.32 kernel) or by disabling Kernel Mode Switching.
Before I start blameing ubuntu, I figured I should do some tests.
My laptop is a Compaq Presario V5306US.  I bought it August 2006. 
Some of the specs:
Processor: AMD Turion(tm) 64 Mobile Technology ML-32
Video: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
Hard Drive: ATA WDC WD800UE-22KVT0  (80G)
Wireless: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

For the test I removed the battery and connected the power supply to a power meter (Watts Up Standard [https://www.wattsupmeters.com/secure/products.php?pn=0](https://www.wattsupmeters.com/secure/products.php?pn=0) )

The Max power drawn during the tests was 53W.

**GRUB**
The first thing I found to be interesting was the power wasted when in the Grub2 menu.
While Grub2 was counting down, the system was drawing 48W. Once the countdown is cancelled (by pressing the down key) the power usage dropped to 45W.  I have noticed that if I leave the grub menu up for a while, the fan will reach its full speed.  I suspect this to be the case with Grub1 also because I remember the fan gradually reaching its full speed then too.  **If you are running on battery, don't stay in the grub menu too long.**

I then tested Windows XP, Ubuntu 10.04, and Ubuntu with 2.6.34 Kernel and the radeon power saving features enabled in xorg.conf (ClockGating, ForceLowPowerMode, DynamicPM):
```

                                                   Power Consumption (in watts)
                                        WinXP           Ubuntu (Lucid Kernel)   Ubuntu (2.6.34)
Boot                                    29-32           27-50                   29-53
Idle Desktop / Wifi On                  18              19                      18
Idle Desktop / Wifi Off                 15              18                      17
Lid Closed / Wifi On                    15              12.1                    12.3
Lid Closed / Wifi Off                   13              11.3                    11.1
Hd Sleep / Lid Open / Wifi Off          -               16.1                    15.0
Hd Sleep / Lid Closed / Wifi Off        -               9                       9


```
*Note: This data was obtained by a single run through each OS, and was performed with intentions of getting a general idea of power consumption.  Windows XP had microsoft security essentials running in the background, but was not actively scanning anything.  Because I used the ac adapter for power readings, Windows may not have been running in a reduced power mode.*

The boot power in ubuntu appeared greater, but what isn't mentioned is the difference in time to boot.  Ubuntu's boot time is much shorter than XP.
The Lucid kernel was 1W higher than the other two.  I suspect that this is due to the power saving features of the video card being disabled.
I was surprized to see that Ubuntu conserves much more power with the lid closed than windows. (I might need to test windows again thought to double check)
Forcing the HD to sleep is simple in ubuntu (hdparm -Y /dev/sda) I don't have a way in windows to force the hd to sleep from a command.  Attempts to wait for the drive to sleep has been uneventful do to the many background applications that keep the hd active.

**laptop-mode-tools**
[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
Disk idling is not enabled by default in Lucid.
Installing laptop-mode-tools offers some extra enhancements.

HD APM is usually set to 254 by default.  This setting essentially disables all power saving features in the hd.
If you notice a High hd temperature try enabling the power saving features:
```

sudo hdparm -B 128 /dev/sda

```
This reduces the temperature and I have notice about an instant 1-1.5W drop in power usage.
laptop-mode-tools has a config file where you can set the apm values:
```

gksu gedit /etc/laptop-mode/laptop-mode.conf 

```
find this section:
```

#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=128
NOLM_AC_HD_POWERMGMT=254

```
I already changed LM_AC_HD_POWERMGMT to 128 on my machine because of the reduction in temperature.
Setting to 128 will enable offloading the heads.  An issue in the past has been that the load counts can get really high with this enabled, and it was speculated that hd failure can occur.  Unloading the head is beneficial because it removes head friction, which leads to heat and power consumption, it also minimizes head damage due to shock.  I have determined that my HD can handle over 600,000 load cycles, and I am currently at 90,000 so I am not concerned about this issue.  Also I am pretty sure high temperatures and mechanical shock is worse than a load cycle.
Part of the reasoning for disabling this feature was because WinXP didn't increase load counts, but in many cases, background applications in Windows never gave the hd a chance to unload the head.

An APM setting of 1 is really aggressive and you may notice your drive spinning up and down constantly...if so you can raise this value to 127 and it should improve.
I have found one cause of the constant spin up and down to be due to firefox's sessionstore feature.  By default firefox will save your active session every 10 seconds...for some reason the writeback buffers get flushed when this happens. (This issue has also been a cause for the high load cycling issues)
An easy fix for this is to go to about:config (in the firefox addressbar) and search for browser.sessionstore.interval
Change the default 10000 (10 seconds) to something like 600000 (5 mins), and restart firefox.
Unfortunately, many websites cycle through ads, this cycling can also cause the drive to spin back up...one solution is to disable flash, another is to use adblock.  In the past someone wrote a how to on how to move your firefox profile into a ramdisk for performance...this could also be used to minimize disk activity.

---

