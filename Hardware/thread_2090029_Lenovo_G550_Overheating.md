---
title: "Lenovo G550 Overheating"
date: 2012-12-01
forum: Hardware
---

### Post by ivotkl on 2012-12-01
OK, so I' ve read a few posts here and none of them led to an useful solution. System is up to date, running Lucid Lynx 10.04 32-bits. As far as I could guess, it might be related to outdated graphic drivers + not applying silicone heat sink compound after cleaning. However, I don' t think that will lower it to normal values. I' ve cleaned it almost performing a complete disassemble of it around a month ago and I' m about to apply silicone.

Relevant code outputs are as follows:

**OS**:
```
Linux ivan-ub 2.6.32-45-generic #99-Ubuntu SMP Tue Oct 16 16:31:11 UTC 2012 i686 GNU/Linux
```

**Graphic card driver** (outdated, search my other posts if you know how to help me with my other current questions):
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```

**grep cooling and grep acpi** (lsmod | grep fan gives no answer):
```
$ dmesg | grep cooling
[    0.380471] processor LNXCPU:00: registered as cooling_device0
[    0.386456] processor LNXCPU:01: registered as cooling_device1
[   16.611604] acpi device:07: registered as cooling_device2
$ dmesg | grep acpi
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[   16.611604] acpi device:07: registered as cooling_device2

```

Solution found so far: open main back cover and place a 60cm. diameter air circulator around 1 m. away from laptop, inclination of about 15, maybe 35 degrees.

After it stopped converting some files and an hour with fan on, temp lowered to 36-ish °C, being initial CPU-cores temp around 102-109 (Being critical 119°, so it was pretty bad).

Hard Disk Drive Temperature was at all times between 37 and 41 Celsius after and during heavy Hard Disk Drive use respectively, don' t know critical values, but I believe they are around 60-70, maybe 75.

Temp log
--------
(Written by me as a description, if needed, to provide further details)

Conditions: outside temperature is around 20°C late in the evening so temp' s gonna drop a bit more. Relative Humidity 73%. Window a bit open, wind direction and speed West - Northwest / 5.6 km/h.

Applications currently opened: chromium-browser with 18 tabs opened, including flash-dependant ones (and maybe java as well); one terminal window with one tab in use and a file browser window. Only current activity I' m doing is writing on this post. Temp2 already on 46 celsius and graphic is in red. I believe is graphic card - which by the way it is an onboard Intel GM45 graphics card with outdated drivers. Fan is still off. Lowering laptop inclination to 0° (back cover still off, temperature is stable). Switched tabs, fan kicked in at low speed. Trying YT HD video (yeah, I'm an a-hole). Playing at 720p. Fan went to mid-speed 2 seconds after it started. Fan' s running a bit faster at 0:17. Placing back-cover again. Well, it seems that temperature is still stable at around 46°C. Copying some files. Temperature on hardware monitor remains the same as per dialogue box opened but it rose to 55°C on terminal (using sensors command). Fan speed raising (Duh!). HDD temp rose to 43°C. Operation ended.

Note for you guys about temp log written: I don' t think sensors installing sensors monitor is helping reduce heat? Will check how temp is when normal using is done and update you once you suggest me to do something about this.

Hope you can help. Shall I inform you any other output, just let me know. Thanks in advanced.

PS: sorry for the long post. I' m trying to give as much information as I can.

---

### Post by gnusci on 2012-12-01
what is the app on top when you run top?

$ top

or

$ htop

---

### Post by ivotkl on 2012-12-01
It actually is Xorg. Maybe outdated drivers? (Mesa are from Dec 2009, no other graphic drivers that I know of are installed that I know of except any that came already with the distro)

By the way, I just turned computer on, opened browser, temperatures are not too high. However, GPU' s temp seems to be between 42 (orange) and 47 (red). Just playing one video and it rose to 51°C (non HD, 360p, non fullscreen). I' ll definitely put some silicone heating compound.

EDIT: Playing another video, same characteristics, temp rose to 59°C (I believe that' s critical as graphic temp was full).

---

### Post by 2F4U on 2012-12-01
Don't underestimate the value of thermal compound. It is necessary to close the gaps between CPU and heatsink. Your overheating issues are most likely due to the absence of a thermal compound.

[http://en.wikipedia.org/wiki/Thermal_grease](http://en.wikipedia.org/wiki/Thermal_grease)

---

### Post by ivotkl on 2012-12-02
Ok, then I'll dismantle and apply it asamdfa (as soon as my daughter falls asleep :haha: ).

Thanks for the help.

**EDIT**: Ok, now temperature rises to 46-47 Celsius when playing HD videos and lowers to 40-43 Celsius when "idle" (right now only with 14 tabs opened on chromium-browser, 720p video still playing on a different tab).

Now, I would like to mark thread as solved but I was wondering if there is any software to modify temperature-dependant fan speed. (I.E. 40°C kick in, 45°C higher speed, 50°C full "throttle").

PS: temp4 (acpi sensor) still rising to 47°C, runtime since powered on (no hibernation, fresh start) is around 4 mins. I believe it is the graphics card. Maybe drivers related (way too outdated)?

Thanks!

---

### Post by ivotkl on 2012-12-02
Shameless bump / update. After a few hours compound was applied, it went back to 45-50°C overheating.

IMO, or it is the fan settings or drivers. Any help?

---

### Post by ivotkl on 2012-12-04
Shameless bump & update: apparently I need to update the BIOS to have some fan speed control over there, but I'm a bit reluctant to do so as I fear it will never come back to life.

---

