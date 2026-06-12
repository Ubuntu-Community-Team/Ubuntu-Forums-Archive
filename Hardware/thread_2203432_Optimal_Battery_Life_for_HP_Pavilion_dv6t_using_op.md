---
title: "Optimal Battery Life for HP Pavilion dv6t using open source drivers"
date: 2014-02-03
forum: Hardware
---

### Post by luca992 on 2014-02-03
I have spent the last few days trying to get optimal battery life out of my hp dv6t QE using the opensource drivers. I have actually gotten it down to an acceptable level. 

The video cards in my dv6:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff)



```



On a fresh boot with full backlight I now get:

14.67 Watts on Average with Standard Deviation 1.39

on a powerstat run.

To accomplish this I am running ubuntu 13.10 and the latest 3.14 rc1 kernel. From my tests power usage seems to be going down with each new kernel release. I am thinking this is happening because of all the updates to radeon dpm.

To check if dpm is working run the command:
```
cat /sys/kernel/debug/dri/65/radeon_pm_info

```
```
cat /sys/kernel/debug/dri/64/radeon_pm_info

```
or 
```
cat /sys/kernel/debug/dri/1/radeon_pm_info

```
I think it may differ by computer/video card

It should list something similar to:
```
default engine clock: 725000 kHzcurrent engine clock: 870800 kHz
default memory clock: 800000 kHz
current memory clock: 24970 kHz
voltage: 1050 mV
PCIE lanes: 16

```

Additionall for dpm

[COLOR=#333333][FONT=UbuntuRegular]You can further configure DPM by opening **/etc/rc.local** and adding the following line:[/FONT][/COLOR]
echo parameter > /sys/class/drm/card1/device/power_dpm_state
[COLOR=#333333][FONT=UbuntuRegular]Where **"parameter"** can be:[/FONT][/COLOR]

[LIST]
[*]**battery** (a set of performance levels targeted for optimal operation on battery)
[*]**balanced** (a set of performance levels targeted for optimal every day use)
[*]**performance** (a set of performance levels targeted for the highest GPU performance)
[/LIST]
source: [http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04](http://askubuntu.com/questions/324733/how-to-enable-the-radeon-dynamic-power-management-feature-in-ubuntu-13-04)
I set mine to **battery**.


Then I updated the opensource graphic drivers to the latest version using oibaf's ppa. Instruction are at
[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

This seemed to reduce the wattage by 1 to 2.

The biggest thing I changed to reduce power usage was to add a few kernel parameters for the intel card.
to change these:
```
sudo gedit /etc/default/grub
```

then edit the line starting with GRUB_CMDLINE_LINUX_DEFAULT to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i915.i915_enable_rc6=7 i915.i915_enable_fbc=1 i915.lvds_downclock=1"
```
save and
```
sudo update-grub
```
*acpi_backlight=vendor is just to make back light controls work on my laptop

Finally I installed laptop-mode-tools with edited cpu config. This brought my power down about and additional 2 watts.

sudo gedit /etc/laptop-mode/conf.d/cpufreq.conf


lines 48-59 as follows:
```
BATT_CPU_MAXFREQ=fastestBATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersave
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=performance
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=performance
NOLM_AC_CPU_IGNORE_NICE_LOAD=0

```


Curiously, TLP actually made my battery life much worse. It increased power used by nearly 10 watts with default settings.

Hope this can help others, and if anyone has additional ways to increase battery please let me know!

EDIT:
Apparently my Radeon card is a not working correctly with DPM because it is a Turks model. I had to manually enable dpm in my kernel parameters. It is not changing power levels correctly at this point with the 3.14 kernel.
[http://www.phoronix.com/scan.php?page=news_item&px=MTU3MzM](http://www.phoronix.com/scan.php?page=news_item&px=MTU3MzM)

---

