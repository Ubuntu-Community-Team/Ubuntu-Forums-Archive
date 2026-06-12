---
title: "T500 just shuts off on low battery (not hibernate / suspend / shutdown)"
date: 2010-02-02
forum: Hardware
---

### Post by tedrogers on 2010-02-02
Hi all,

When my laptop battery gets to 5% or something, the T500 just shuts off completely...no graceful hibernate, suspend or shutdown.

Power manager settings seem ok. Worked reasonably well on my old T42.

BIOS settings are all set to shutdown and give warning beeps. Ubuntu 9.10 seems to ignore this.

No warning, no beeps, just power off!

Anyone know why this might happen?

Thanks.

---

### Post by cebif on 2010-02-02
> **tedrogers said:**
> Hi all,

When my laptop battery gets to 5% or something, the T500 just shuts off completely...no graceful hibernate, suspend or shutdown.

Power manager settings seem ok. Worked reasonably well on my old T42.

BIOS settings are all set to shutdown and give warning beeps. Ubuntu 9.10 seems to ignore this.

No warning, no beeps, just power off!

Anyone know why this might happen?

Thanks.
I don't know if I can provide a solution. Just a few suggestions. Have you tried to see if a manual initiated hibernate, suspend or shutdown works.
In the Power Management general tab, "When the power button is pressed", choose one of these from the dropdown menu.
Of course it will be necessary for power settings in the BIOS to have, 4 second delay when power button pressed, which you have probably already done.

---

### Post by tedrogers on 2010-02-03
I intended to try this but I was power cycling my battery last night and so didn't get round to it.

I will investigate and report back.

---

### Post by tedrogers on 2010-02-03
So, I tried all of the possible combinations of Suspend and Hibernate when pressing power button and closing lid, and apart from the usual graphics corruption coming out of hibernation, it all works flawlessly and in the same way as I've experienced it on my older T42.

So it all works you could say! Just not when I get critically low battery! :( :(

Any ideas anyone?

---

### Post by cebif on 2010-02-03
> **tedrogers said:**
> So, I tried all of the possible combinations of Suspend and Hibernate when pressing power button and closing lid, and apart from the usual graphics corruption coming out of hibernation, it all works flawlessly and in the same way as I've experienced it on my older T42.

So it all works you could say! Just not when I get critically low battery! :( :(

Any ideas anyone?
I have not got a laptop just a desktop so I don't know if I can help much but is there some setting available to suspend, hibernate or shutdown when the battery is discharged to a lessor degree. It looks like the battery might be getting so discharged that there is not enough power or time left to shutdown cleanly.
Are you using gnome or kde? I think there is more flexible settings available in kde than gnome with power settings. It might be possible to download extra power setting widgets for laptops in gnome.

---

### Post by tedrogers on 2010-02-03
Hi,

Running gnome.

Yeah all the settings are ok. It is set to shutdown on low power on battery. I just don't understand why it just goes off!

I don't have any option to change the percentage point at which it starts shutdown though or anything else.

---

### Post by cebif on 2010-02-03
> **tedrogers said:**
> Hi,

Running gnome.

Yeah all the settings are ok. It is set to shutdown on low power on battery. I just don't understand why it just goes off!

I don't have any option to change the percentage point at which it starts shutdown though or anything else.
If you've got laptop-mode-tools installed and it looks like you have, it should work unless your battery is getting old and is discharging at a faster rate than the program can allow for. As far as I know a low setting for shut-down should be adequate. If you installed wmbattery (Window Maker program but works in gnome). It displays the battery status, high low or critical. Disable the automatic shut-down on battery status for the other program. Monitor the battery status manually when it reaches low try shutting down to see if there is enough time for a clean shutdown.

---

### Post by tedrogers on 2010-02-03
Yes, laptop-mode-tools is installed...and it is a brand new battery!!! :confused:

---

### Post by cebif on 2010-02-03
> **tedrogers said:**
> Yes, laptop-mode-tools is installed...and it is a brand new battery!!! :confused:
I don't know if batteries are swappable or compatible in laptops but could you try another battery from one of your other laptops? Was the laptop shutting down cleanly on low battery before you replaced with the new one?

---

### Post by tedrogers on 2010-02-04
No, the older battery was so dead it held no charge at all...couldn't even test that I'm afraid.

Thanks for your suggestions though.

---

### Post by cebif on 2010-02-04
> **tedrogers said:**
> No, the older battery was so dead it held no charge at all...couldn't even test that I'm afraid.

Thanks for your suggestions though.
Try installing wmbattery then start it from the terminal. Monitor it when your at your computer, for when it indicates low battery then try suspending, shutting down or hibernating.
That way you will definitely know if it is the new battery or a power manager problem

---

### Post by cebif on 2010-02-04
Before the old battery lost its charge holding ability was the laptop able to shutdown automatically when the battery got low?

---

### Post by tedrogers on 2010-02-04
The laptop would shut down immediately because the battery was so low / old...but as farf as I can recall it actually did shutdown rather than simply go off!

What are you thinking here?

---

### Post by cebif on 2010-02-04
> **tedrogers said:**
> The laptop would shut down immediately because the battery was so low / old...but as farf as I can recall it actually did shutdown rather than simply go off!

What are you thinking here?
I was thinking if it wasn't that long ago before the old battery went bad, and if you had not obtained any automatic updates for power management, then it is not a software problem but hardware.
Did the previous battery last very long?
It looks quite a long time though from when you recall the old battery and shutdown worked.
To be certain try installing wmbattery as I posted before and while your at your laptop monitor the icon for low battery then try to shutdown. If you cannot shutdown cleanly manually then it definitely is hardware.

---

### Post by tedrogers on 2010-02-05
> **cebif said:**
> I was thinking if it wasn't that long ago before the old battery went bad, and if you had not obtained any automatic updates for power management, then it is not a software problem but hardware.
Did the previous battery last very long?
It looks quite a long time though from when you recall the old battery and shutdown worked.
To be certain try installing wmbattery as I posted before and while your at your laptop monitor the icon for low battery then try to shutdown. If you cannot shutdown cleanly manually then it definitely is hardware.

The older battery was DOA in the laptop (2nd hand), so I can't test that.

All power saving features work fine in this T500 laptop under Windows 7...it can't be a hardware issue.

I will have a look into wmbattery anyway and see if it throws anything obvious up.

Thanks.

---

### Post by tedrogers on 2010-02-05
Okay, I think I've hit on something significant.

With wmbattery running, and the battery discharging, the terminal continually reports

```
unknown battery state
```

So I guess the battery isn't reporting its state, or Ubuntu isn't reading it properly.

However, the wmbattery widget thing will tell me how long it has left and a reasonably accurate guess on remaining capacity.

What on earth is going on???

:confused:

---

### Post by rshetye on 2010-02-05
your battery is bad and incorrectly reports the amount of time left... hence laptop does not actually get enough time to hibernate...

---

### Post by cebif on 2010-02-05
> **rshetye said:**
> your battery is bad and incorrectly reports the amount of time left... hence laptop does not actually get enough time to hibernate...
I thought it might be the battery but as tedrogers said in previous post all power saving works in windows 7.

---

### Post by cebif on 2010-02-05
> **tedrogers said:**
> Okay, I think I've hit on something significant.

With wmbattery running, and the battery discharging, the terminal continually reports

```
unknown battery state
```

So I guess the battery isn't reporting its state, or Ubuntu isn't reading it properly.

However, the wmbattery widget thing will tell me how long it has left and a reasonably accurate guess on remaining capacity.

What on earth is going on???

:confused:
Well is just about as far as my level of knowledge will allow. The only thing I can suggest now is:
1. reinstall laptop-mode-tools, restart and see if that works.
2. Install acpitool-dbg. According to synaptic it is a command line toll for "accesses the /proc/acpi or /sysfs entries to get or set ACPI values"  I have never used or needed to use this, so if you had any questions I might have to hand the problem over to someone else.
Hope you get it solved.

---

### Post by tedrogers on 2010-02-05
Well thanks for your help anyway Cebif...I appreciate it. :)

And as for acpitool....all it does is this:

```
  Battery #1     : charged, 99.96%
  AC adapter     : on-line 
  Thermal zone 1 : ok, 41 C
  Thermal zone 2 : ok, 34 C
```

...and this:

```
  Battery #1     : discharging, 99.96%, 01:44:47
  AC adapter     : off-line 
  Thermal zone 1 : ok, 39 C
  Thermal zone 2 : ok, 34 C
```

Seems it thinks the battery is ok! :) If only it *really* knew. ;)

---

### Post by cenzorrll on 2010-02-05
open gconf-editor in a terminal and go to apps>gnome-power-manager>actions

```
gconf-editor
```

you should see options for critical battery, critical ups, etc.

under critical battery it should say either suspend or hibernate.

also, in thresholds you can set the percentage at which your computer goes to suspend/sleep.

i would change these values to a higher percentage and try it again to see if it helps.  also keep in mind that if it's set to suspend, you still use power to keep everything in ram, and once power is out. bye bye saved work.  hibernate saves everything to disk but you still go through the boot sequence (you also need enough swap space to do so).

---

### Post by tedrogers on 2010-02-06
Okay, so I changed my percentage_critical and percentage_action values to 6 and 5 respectively.

Fingers crossed that will work.

Thanks for your assistance.

---

### Post by tedrogers on 2010-02-07
Okay so 6% didn't work...if I have the shutdown on 6% then it still just shuts off...however if I have it higher at 8% then it works fine. :)

Seems like the battery isn't accurately reporting remaining capacity...it is a cheapo!

You get what you pay for I suppose...why do I never learn?

Thanks for solving it though. :)

---

