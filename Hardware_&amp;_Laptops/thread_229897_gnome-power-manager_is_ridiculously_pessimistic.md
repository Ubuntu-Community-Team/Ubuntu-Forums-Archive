---
title: "gnome-power-manager is ridiculously pessimistic"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by saffsd on 2006-08-05
Hello all. Just completed a clean install of dapper on a hp zt3000. Everything working pretty darn good out of the box, except one major annoyance: gnome-power-manager is getting the estimates of battery life remaining all wrong!

Typically it may read something like "2 minutes remaining (50%)"

everything looks fine in /proc/acpi. Works fine when charging too. Also, it works for a little while when just switched to battery power. For example, I just unpluged the power cord, and it said "20 minutes remaining (19%)". Now, about 30 seconds later, i got a "critical battery" warning, claiming "3 minutes remaining (19%)"

```

/proc/acpi/battery/C11F# cat state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1400 mA
remaining capacity:      608 mAh
present voltage:         14818 mV

```

```

/proc/acpi/battery/C11F# cat info
present:                 yes
design capacity:         2948 mAh
last full capacity:      2948 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 295 mAh
design capacity low:     0 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           00 30 11 84 00 64 55 00
battery type:            LIon
OEM info:                 Hewlett-Packard

```

The popups this produces are very annoying, as every 30 seconds or so I get a "critical action" warning even when the battery is half-full. I've also had to stop gnome-power-manager from turning off my machine when it detects power low (as this was also being triggered at about 50% battery). I'm not that familiar with the internals of the gentopia stack, but I'm figuring that the problem is in the code that estimates the battery life remaining, as the /proc/acpi/battery interface is reporting correctly.

Here's some package versions:
gnome-power-manager 2.14.3-0ubuntu11
hal 0.5.7-1ubuntu18
dbus 0.60-6ubuntu8
linux-image-2.6.15-26-386 2.6.15-26.46

```

uname -a
Linux laptop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

```

Any suggestions/help much appreciated! Thanks!

---

### Post by reech on 2006-08-05
On xbuntu here .Exactly the same problem though - asus laptop. Suspend/shutdown also seems to have been broken since last update.

---

### Post by hughsient on 2006-10-27
> **saffsd said:**
> 
Typically it may read something like "2 minutes remaining (50%)"

Sounds like you need a HAL update. You're battery rate reports in mAh and this causes HAL to sometimes give values to g-p-m that are three powers of magnitute too large. There's lots more details about this in the HAL archives.

Richard Hughes.

---

### Post by Buggin on 2006-11-17
I have the exact same problem on a zt3000. I get the same results no matter if I drain thebattery down to 10% or use it fully charged. I'm going to try installing the newest version of hal and gnome power manager and see if that fixes it. I'll let you know.

---

### Post by Buggin on 2006-11-18
I didn't have any luck installing the newest gnome-power-manager. Instead I came up with a workaround. You'll lose suspend and hibernate support. Well really all power management but those popups are annoying so to me it's worth it. 

I just went to System> Preferences> Sessions and in the Startup Programs tab I disabled gnome-power-manager. Then, to get a reading on your charge levels you right click on one of your panels and go to Add To Panel. In the System & Hardware section click on Battery Charge Monitor and click + Add


That's it. No more annnoying popup windows or forced shutdowns. It's not a fix but it's at least a workaround until it gets fixed in future updates.

---

### Post by Alveric on 2007-01-19
> **Buggin said:**
> I didn't have any luck installing the newest gnome-power-manager. Instead I came up with a workaround. You'll lose suspend and hibernate support. Well really all power management ...

I just went to System> Preferences> Sessions and in the Startup Programs tab I disabled gnome-power-manager. Then, to get a reading on your charge levels you right click on one of your panels and go to Add To Panel. In the System & Hardware section click on Battery Charge Monitor and click + Add

Hi, I'm getting similar problems in Edgy - gnome power manager reads the battery as 100% then 66% then 33% then zero; I've been told I need to try out the newer version of HAL than is in the repositories but am a total newbie - just tried to install it (HAL 0.5.8.1) and got an error message that there was no valid C compiler in the path (? - I know what a C compiler is but really don't know what to do about this message...).

Anyway, I can live without hibernate - what I need is a meaningful battery readout (did I mention I get meaningful readouts by running acpi in the shell?)

Can you tell me - if I did as you suggested (2 months ago... yes, I'm behind the times) will that also kill off the cpu frequency scaler or is that a separate deal?

Al.

---

### Post by Alveric on 2007-01-22
I tried this out (I do get to keep the cpu-freq applet).

When I rebooted, gnome power manager had still loaded.

More, the battery status applet was mirroring what gnome power manager said (which I know is wrong because I tried acpi in the shell).

Al.

---

