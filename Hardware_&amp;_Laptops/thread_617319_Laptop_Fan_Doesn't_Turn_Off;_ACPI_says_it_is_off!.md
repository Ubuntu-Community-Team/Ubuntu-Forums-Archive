---
title: "Laptop Fan Doesn't Turn Off; ACPI says it is off!"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by Arthur Archnix on 2007-11-19
I'm running Gutsy [uname = 2.6.22-14-generic #1 SMP i686 GNU/Linux] on an HP530 laptop, and the fan runs constantly at a low speed. I can hear it running, and I can feel it pushing cool air if I put my fingertips to the exhaust. It should turn off when the temp is low enough.

Note the temps below, and the fact that the fans (why four?) are supposedly "off", despite the fact that I can hear and feel the fan. Could polling = disabled have anything to do with this?

**cat /proc/acpi/thermal_zone$ ls**
```
TZ0  TZ1  TZ2  TZ3  TZ4
$:/proc/acpi/thermal_zone$ cd TZ0
$:/proc/acpi/thermal_zone/TZ0$ cat state
state:                   ok
$:/proc/acpi/thermal_zone/TZ0$ cd /
$:/$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
<polling disabled>
state:                   ok
temperature:             37 C
critical (S5):           256 C
active[0]:               76 C: devices=C2FE 
active[1]:               70 C: devices=C2FF 
active[2]:               62 C: devices=C300 
active[3]:               55 C: devices=C301 
<setting not supported>
<polling disabled>
state:                   ok
temperature:             41 C
critical (S5):           85 C
passive:                 83 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1 
<setting not supported>
<polling disabled>
state:                   ok
temperature:             37 C
critical (S5):           102 C
<setting not supported>
<polling disabled>
state:                   ok
temperature:             28 C
critical (S5):           85 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1 
<setting not supported>
<polling disabled>
state:                   ok
temperature:             0 C
critical (S5):           110 C
```

**cat /proc/acpi/fan/*/***
```
status:                  off
status:                  off
status:                  off
status:                  off
```

---

### Post by arkara on 2007-11-19
so where is the problem that the fan does not turn off.
it constantly keeps your system cool.
anyway if it bothers you. check if you boot with acpi=off.
if that happens this is the reason for your fan turning.
try to boot with acpi=on and post back what happens.

---

### Post by Arthur Archnix on 2007-11-19
I don't boot with ACPI=off
```
title           Ubuntu 7.10
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ba8c9288-46d8-4bcc-b03a-891fa298f4dd ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```

I have the latest bios available from HP, and there is a setting for "Fan Always On While on AC Power". It's default setting is disabled. I enabled it and rebooted and noticed no change. I then disabled it and rebooted again.

It's not just that it's annoying. It also affects battery life, and fan life (I would assume) as well. To say nothing of the discrepancy between what I can hear and feel and what ACPI is reporting.

**EDIT: We're talking low, low noise here, which I might even think was just the hard-drive operating if it wasn't for that fact that my fingertips can feel cool air being pushed out of the fan exhaust. What else could explain that except a low spinning fan?**

---

### Post by Arthur Archnix on 2007-11-20
Bump.

---

### Post by Arthur Archnix on 2007-11-21
bump 2 of 3.

---

### Post by Arthur Archnix on 2007-11-22
bump 3/3.

---

### Post by Tweenk on 2007-11-22
1. Check if you have iTCO_wdt and / or iTCO_vendor_support in the output of lsmod. This is known to disable ACPI sometimes (or I heard so). This driver is for the watchdog timer - you will not need it. Blacklist this driver (add "blacklist iTCO_wdt" and "blacklist iTCO_vendor_support" to /etc/modprobe.d/blacklist) and restart
2. Some BIOSes think they are more competent at handling your fans, and will not let you tinker with them or report their state via ACPI. This is the case with TC1100 - temperature is reported, and I can see a corellation between it and when the fans kick in, but the critical temperatures are completely different from what is listed in /proc/acpi/thermal_zone. echo 3 > /proc/acpi/fan/FAN0/state doesn't work either.

---

### Post by Arthur Archnix on 2007-11-23
Thanks for the tip. I searched for the bug reports about iTco, and although I did have those loading blacklisting them hasn't made a noticeable difference. 

On what I'm sure is a related though, for the first time (after blacklisting iTCO, coincidence?) my laptop fan stayed on full blast after boot. Usually it boots, spins up and then spins down as acpi is loaded and it sees that the CPU temps are cool. This time is stayed full blast. I looked at output of acpi-V and all temps were cool at 20, except for thermal 5 which was 86, some impossible temperature considering it was my first time turning it on in 6 hours and its in a cool basement. I rebooted and fan problem did not reoccur, and acpi -V showed cool temps across the board.

---

