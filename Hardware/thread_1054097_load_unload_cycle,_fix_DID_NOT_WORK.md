---
title: "load unload cycle, fix DID NOT WORK"
date: 2009-01-29
forum: Hardware
---

### Post by redbeardmcg on 2009-01-29
I performed [This FIX]("https://wiki.ubuntu.com/PowerManagement#How%20to%20get%20disks%20idleing%20correctly%20(without%20excessive%20load%20cycling)") and I still have the issue. I can actually hear the disk in my laptop spin up/down so frequently that I moved it and threw a coat over it so I could work. The load_cycle is EXTREMELY high, in fact the manufacturer suggests this drive should not last much past 610,000 and it is over 640,000 now!!! This is a work machine and I desperately need a fix. 

I am running 8.10, and set "ENABLE_LAPTOP_MODE=true" which fixed nothing.

sudo smartctl -a /dev/sda|grep -i load_cycle
193 Load_Cycle_Count      .....     **_642053_**

-Ryan

---

### Post by redbeardmcg on 2009-01-29
** BUMP **

This is a serious issue that has an open and active bug which recommends a fix that does not work. Has anybody else confirmed that the fix does not work on their machine?

Is there a different forum for non-"how do i get my ipod thingy working in my linux thingy" questions?

-Ryan

---

### Post by GrouchoMarx on 2009-01-31
The fix also doesn't work for me. x200 thinkpad, Seagate ST980817AS. Load Cycle count increases every 5 seconds on battery power. Obviously this is a complicated problem as they haven't been able to fix it for quite some time. The main thread on this bug is here: [laptop harddrive Load_Cycle_Count issue]("http://ubuntuforums.org/showthread.php?t=805570&highlight=load+cycle")

---

### Post by GrouchoMarx on 2009-02-01
I've found two solutions that solve the problem. I'm not sure which is prefered, but both work. It's good practice to make backups of any files before you change them:

1) If you set "ENABLE_LAPTOP_MODE=true" in "/etc/default/acpi-support", then you must also change "BATT_HD_POWERMGMT=**1**" to "BATT_HD_POWERMGMT=**254**" in "/etc/laptop-mode/laptop-mode.conf".

2) If you don't want to enable laptop-mode, then in "/etc/acpi/start.d/90-hdparms.sh", "/etc/acpi/resume.d/90-hdparms.sh", "/etc/acpi/battery.d/90-hdparms.sh", and "/etc/acpi/ac.d/90-hdparms.sh" change:
```
	if [ "$STATE" = "BATTERY" ] ; then
	  hdparm -B **128** $dev
	else
	  hdparm -B 254 $dev

```
to
```
	if [ "$STATE" = "BATTERY" ] ; then
	  hdparm -B **254** $dev
	else
	  hdparm -B 254 $dev

```

Note that the number 254 will eliminate Load_Cycles completely. Normally, you would not want to completely eliminate Load_Cycles as they are a useful power-saving feature and can help protect the drive from physical damage during motion. Ideally there should be ~15/hour while on battery power. But since your hard drive is already past its limit, you might as well eliminate them. Just be careful not to jostle the laptop around too much.

Hope that helps.

---

