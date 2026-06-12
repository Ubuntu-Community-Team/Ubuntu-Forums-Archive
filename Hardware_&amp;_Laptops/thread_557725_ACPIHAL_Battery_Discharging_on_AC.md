---
title: "ACPI/HAL Battery Discharging on AC"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by jbmech006 on 2007-09-23
Hello,

I have been searching these forums and the net for months looking for a fix for my battery problem. I did find some articles stating that HAL was not functioning properly and this is a bug with this kernel. My problem is that my laptop battery discharges while on AC power. Is there a fix for this that I overlooked? Thanks for your guy's help. 


Here are some specs for my system:

Feisty Ubuntu 7.04
Toshiba Satellite M100 
12 Cell Battery
Intel Centrino Core Duo T2400 / 1.83 Ghz

$uname -a
     Linux nanode 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

$acpi -V 
     Battery 1: [COLOR="Red"]_discharging,_[/COLOR] 66%,  remaining
     No support for device type: thermal
     AC Adapter 1: [COLOR="Red"]_on-line_[/COLOR]

$hal-find-by-capability --capability battery
     /org/freedesktop/Hal/devices/acpi_BAT1

$cat /proc/acpi/battery/BAT1/info
    present:                      yes
    design capacity:         8600 mAh
    last full capacity:         8600 mAh
    battery technology:     rechargeable
    design voltage:            11100 mV
    design capacity warning: 420 mAh
    design capacity low:     258 mAh
    capacity granularity 1:  264 mAh
    capacity granularity 2:  3780 mAh
    model number:            PA3400U 
    serial number:           3658Q
    battery type:            Li-Ion
    OEM info:                TOSHIBA

$cat /proc/acpi/battery/BAT1/state
    present:                        yes
    capacity state:              ok
    charging state:              discharging
    present rate:                 0 mA
    remaining capacity:      5160 mAh
    present voltage:           11100 mV

---

### Post by aethralis on 2007-10-24
I have had no problems with the battery and just now suddenly I get similar messages "battery discharging", and I'm on AC power? Lenovo 3000 N100... Any ideas?
____
Never mind that... extension cord was disattached... somehow.

---

### Post by jbmech006 on 2007-11-08
Hi Again,
Due to the lack of responses I guess not many people are having this problem. I upgraded to Gusty with high hopes that my battery discharging problems would be magically fixed. However they still exist. One interesting thing is when I started up Gusty for the first time I got a message that my battery "might" be one of the batteries being recalled by Toshiba due to a manufacturing defect. 

I went to Toshiba's recall website and my battery serial number is not one of the ones that is being recalled. It makes me wonder if somewhere in the ACPI code my battery recharge capabilities are disabled because of the possability that it could be defective. Does any one have any ideas on how I would check my preposterous conspiracy theory? :) Thanks for any help you guys have.

---

### Post by figgles on 2007-12-08
I can't say that my post nails it, but I am seeing the same problem. I thought it was a hardware problem on mine (bad AC or battery), except that I have 2 batteries (one new, one 2 years old) and they exhibit the same problem (discharge despite being AC online) For kicks I booted into the Gutsy image CD and now it is charging. Yes, it charges while in shutdown. I'd love to know the fix without reloading the OS

---

### Post by figgles on 2007-12-18
> **figgles said:**
> [snip]Yes, it charges while in shutdown. I'd love to know the fix without reloading the OSContinuing on, I've found a work-around. Shutdown your laptop and disconnect and then reconnect your battery. The battery then charges as it should. I have two batteries and both exhibit the same behavior.

---

### Post by jbmech006 on 2008-05-31
Cool someone responded! I had given up hope and went back to Win XP. I tried out your idea of shutting down and reinserting the battery. I installed 8.03 Hardy, The battery charged to 70% then started discharging while still on AC power. I hold my head in sorrow and dread the thought of going back to XP... :frown:

$acpi -V 
Battery 1: charging, 70%, charging at zero rate - will never fully charge.
No support for device type: thermal
AC Adapter 1: on-line

a few seconds later...

$acpi -V 
Battery 1: discharging, 70%,  remaining
No support for device type: thermal
AC Adapter 1: on-line

:confused:

Battery Info:
present:                 yes
design capacity:         8600 mAh
last full capacity:      8600 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3399U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                TOSHIBA

cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      5762 mAh
present voltage:         11100 mV

](*,)

---

### Post by rreese6 on 2008-06-06
I am having the same issue in Gutsy.
I am using kpowersave.
Interestingly, I close kpowersave, then restart hal
under System Settings>>Advanced>>System Services.
Then I restart kpowersave and it shows the battery and the charge rate.
Of course the issue returns after I reboot so I suspect that hal might be starting too soon in the boot up process....If that makes sense.

Any thoughts about making this a permanent fix?

[COLOR="Red"]**********UPDATE *************
June 7 2008[/COLOR]

[COLOR="Black"]Since yesterday, I have removed Kpowermanager and am using the guidance power manager (Kubuntu Gutsy 7.10)
Once I am on the desktop the power manager doesn't show the battery information.
I restart hal , log off and on and the power manager now shows the battery, very strange.[/COLOR]

[COLOR="Red"]******************************[/COLOR]

---

### Post by rreese6 on 2008-06-06
> **jbmech006 said:**
> Cool someone responded! I had given up hope and went back to Win XP. I tried out your idea of shutting down and reinserting the battery. I installed 8.03 Hardy, The battery charged to 70% then started discharging while still on AC power. I hold my head in sorrow and dread the thought of going back to XP... :frown:

$acpi -V 
Battery 1: charging, 70%, charging at zero rate - will never fully charge.
No support for device type: thermal
AC Adapter 1: on-line

a few seconds later...

$acpi -V 
Battery 1: discharging, 70%,  remaining
No support for device type: thermal
AC Adapter 1: on-line

:confused:

Battery Info:
present:                 yes
design capacity:         8600 mAh
last full capacity:      8600 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3399U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                TOSHIBA

cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      5762 mAh
present voltage:         11100 mV

](*,)

I also had the charging issue on my Toshiba laptop.
it would only charge to 65%. turned out to be a bad battery.
Once I changed the battery, charging when to 100% and remained like that for the past year.

---

### Post by mrroland on 2008-07-06
I have a compaq evo n600c. Since upgrading to kubuntu 8.04 i get random messages from the battery manager that the battery has been removed... battery manager does not shows the battery anymore ather the message. Also i have strange crashes (instant poweroff)
but i'm investigating or this is caused by adding a extra dimm.

---

