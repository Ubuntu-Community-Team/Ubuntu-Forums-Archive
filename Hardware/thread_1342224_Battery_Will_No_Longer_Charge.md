---
title: "Battery Will No Longer Charge"
date: 2009-11-30
forum: Hardware
---

### Post by stew721 on 2009-11-30
I have a Dell Inspiron 1525 and have been having issues charging the battery as of late.  I've searched the 'net and have seen countless discussions regarding the issue, but none of which that have helped me so far.

I used to be able to disconnect and reconnect the AC adapter from the laptop several times to get it to start charging, but that's no longer working though.  My battery's now sitting at 0%, but Ubuntu is saying it's charged and refusing to charge it.

The BIOS shows the battery as being 0% charged and idle.  The AC adapter has only ever been recognized once by the the BIOS the entire time that I've owned this notebook and the one time it did, it was displayed as 65W in the BIOS.

I was considering getting a 90W universal smart charger, but would like some opinions before spending the $101.50 on it though as I'm not even sure it would resolve the issue.  The other thing I should mention is that it has only ever charged while powered off the one time that th AC adapter was recognized by the BIOS.  Other than that time, the battery's always been charged while I'm using the notebook.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid
``````
$ uname -a
Linux 2MUMT6PJ 2.6.30.7 #1 SMP Fri Sep 18 15:36:50 PDT 2009 i686 GNU/Linux
``````
$ cat /proc/acpi/battery/BAT0/alarm
alarm:                   unsupported
``````
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         5200 mAh
last full capacity:      4004 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 520 mAh
design capacity low:     157 mAh
capacity granularity 1:  52 mAh
capacity granularity 2:  52 mAh
model number:            DELL XR6948
serial number:           18
battery type:            LION
OEM info:                Sanyo
``````
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          critical
charging state:          charged
present rate:            1 mA
remaining capacity:      0 mAh
present voltage:         10935 mV
``````
$ acpi -abt
     Battery 0: Unknown, 0%
  AC Adapter 0: on-line
     Thermal 0: ok, 43.0 degrees C
```

---

### Post by stew721 on 2009-12-01
Alright, I was out this morning anyhow and went ahead and got a new 90W smart AC adapter (APA23US) from Targus.

My notebook was powered off when I switched the AC adpaters and it did not appear to be charging while powered off.  I then removed both the AC adapter and the battery.  At this point I held the power button on the notebook for about 30-45s; after which I connected the AC adapter and turned on the computer.  When I logged in, the tray icon showed that the battery was installed and fully charged (solid green) even though the battery was sitting on the desk beside the computer. I inserted the battery and the charging light on the front of the notebook flashed blue for a split-second and went off again. I waited for a few minutes with no status change. I then proceeded to remove the battery and restart the computer. When I logged in again, the tray icon still showed the battery was inserted and fully charged.

At first, I'd thought perhaps it was the battery.  However, the tray icon was reporting there was a fully charged battery in the computer when in fact there was none at all.  That would be the system, not the battery as it's not even installed.  Also, if I click on the tray icon to open Power Manager, the "Battery Powered" section is now greyed out and I can make no changes to that area.

If I check the battery status from the terminal, it appears to be properly seen as installed/removed.  However, the tray icon no longer reflects this properly, nor can I make any changes to the battery section of Power Manager.  Does anybody have any suggestions for me with regards to my issue(s)?

Below is while the battery's installed:
```
$ acpi -abt
     Battery 0: Unknown, 0%
  AC Adapter 0: on-line
     Thermal 0: ok, 44.0 degrees C
``````
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         5200 mAh
last full capacity:      4004 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 520 mAh
design capacity low:     157 mAh
capacity granularity 1:  52 mAh
capacity granularity 2:  52 mAh
model number:            DELL XR6948
serial number:           18
battery type:            LION
OEM info:                Sanyo
``````
$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          critical
charging state:          charged
present rate:            1 mA
remaining capacity:      0 mAh
present voltage:         10928 mV
```Below is while the battery's removed:
```
$ acpi -abt
  AC Adapter 0: on-line
     Thermal 0: ok, 44.0 degrees C
``````
$ cat /proc/acpi/battery/BAT0/info
present:                 no
``````
$ cat /proc/acpi/battery/BAT0/state
present:                 no
```

---

### Post by oOarthurOo on 2009-12-01
I've experienced a similar problem with an HP530. The battery suddenly died one day while using 8.1. Since then, I bought a replacement battery which lasted about a month, then refused to hold a charge. I installed windows seven, but that did nothing. I've tried your tricks as well, but no joy.

Frankly I've chalked this up to either bad batteries or bad hardware, some kind of hardware problem inside the laptop. 

In terms of trouble shooting your own problem, try to find another laptop that accepts your battery and see if it can charge it. 

A friends Dell also had the battery die suddenly, and researching online I found a lot of complaints but no resolution. If I were you I'd return the $110 charger. That's 1/4 the cost of a new laptop. :)

---

### Post by Grenage on 2009-12-01
The charging section of laptops accounts for a lot of these problems.  They seem to just.. die.

---

### Post by stew721 on 2009-12-01
I've now noticed that the battery indicator on the front of the computer flashes four orange/amber and then one blue when I insert the battery; after that, it goes dark again.  From what I've been able to find on the 'net, this indicates a temporary battery failure which is generally due to the battery overheating.  However, the problem with that is that I get that light combination even if the battery's been out for some time and even after the computer itself has been off as well.  So there would be no overheating in those instances. This doesn't explain why the tray icon indicates the battery's installed and fully charged when it's in fact not even in the computer either though. If I go into Power Manager, the battery section is no longer greyed out either.  :^)

---

