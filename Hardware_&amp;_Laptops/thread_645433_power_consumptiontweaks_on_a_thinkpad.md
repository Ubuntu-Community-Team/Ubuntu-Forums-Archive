---
title: "power consumption/tweaks on a thinkpad?"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by mma8x on 2007-12-20
i have a thinkpad r61, and am trying to get a feel for what kind of power consumption people are seeing.  i have gutsy installed with a custom 2.6.24 x_64 kernel.  finally got everything working, and am seeing 13.0W at idle, screen on the dimmest setting.  with the screen brightened up a click or 2, surfing the web costs me 15-16W.  stuff i've done:
1.  i'm running kpowersave for cpu freq scaling.
2.  laptop-mode
3.  here are a few tweaks that i just threw into a simple script; these suggestions were taken from lesswatts.org and powertop:
```
#! /bin/bash
#'sched_mc_power_savings' tunable under /sys/devices/system/cpu/ controls the Multi-core related tunable. By default, this is set to '0' (for optimal performance). By
#setting this to '1', under light load scenarios, the process load is distributed such that all the cores in a processor package are busy before distributing the
#process  load to other processor package
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
#disable wake on lan
ethtool -s eth0 wol d
#wifi
echo 7 > /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level
#disable cd-rom polling
hal-disable-polling --dev /dev/hda
#disable uhci-hcd module
rmmod uhci-hcd

```

note that my wifi (iwl3945) isn't working with iwpriv anymore.  i don't know why.
there's a kernel patch relating to sata on lesswatts.org that i wasn't able to apply.  anyone else have any tricks/suggestions?  also, does anyone know where i can put this script so that it's run automatically when switched to batt power?

---

### Post by zyghom on 2007-12-20
why not checking status of ac-adapter ?
 cat /proc/acpi/ac_adapter/ADP1/state
every minute in crontab and then if offline then start script else stop script ?

---

### Post by Scarath on 2007-12-20
have you checked out [thinkwiki.org]("www.thinkwiki.org")? there may be more solutions there

---

### Post by mma8x on 2007-12-20
> **zyghom said:**
> why not checking status of ac-adapter ?
 cat /proc/acpi/ac_adapter/ADP1/state
every minute in crontab and then if offline then start script else stop script ?

well, for one thing i'd rather not have the overhead of a cron script running every minute.  for another, a more elegant solution would be for the script to run when acpi detects a switch to battery power--that's possible, but i'm not sure where to place the command. maybe somewhere in laptopmode-tools.conf?

@scarath:

yes, i've checked out thinkwiki.  lots of helpful info.  just wondering if anyone has done anything different, or is seeing significantly different power consumption--for some reason i'm having a hard time finding this info.

---

### Post by zyghom on 2007-12-21
what about /etc/acpi/events/battery ?

```
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh

```

---

### Post by mma8x on 2007-12-21
that looks more like what i'm looking for...
not sure how to implement it though.  tried adding the line:
```
action=/path/to/script
```
without success.  not sure if that's the syntax to use.

---

### Post by zyghom on 2007-12-22
of course after changes you restarted acpid right ?  :)

---

### Post by mma8x on 2007-12-22
sure, after you mentioned it :)
it works now for getting on battery, but the reverse script doesn't apply when placed in /etc/acpi/events/ac...

---

### Post by mma8x on 2007-12-24
ok, i think i finally figured it out.  i stole part of a script from [ [COLOR="Blue"]here]("http://www.thinkwiki.org/wiki/ACPI_action_script_for_battery_events")[/COLOR], modified it, and inserted it into the end of /etc/acpi/power.sh.  it now works.  looks like that for whatever reason, both scripts were run (both in /etc/acpi/events/battery and ac), regardless of whether the action was change to or from ac/battery:

from /var/log/acpid (note that this is one event, and both powersaving.sh and powersaving_on_ac.sh were run):
```
[Sun Dec 23 08:26:19 2007] received event "ac_adapter AC 00000080 00000001"
[Sun Dec 23 08:26:19 2007] notifying client 5139[107:116]
[Sun Dec 23 08:26:19 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:19 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:19 2007] executing action "/home/abatzis/Scripts/power_on_ac.sh"
[Sun Dec 23 08:26:19 2007] BEGIN HANDLER MESSAGES
Polling for drive /dev/hda have been enabled. The fdi file deleted was
  /etc/hal/fdi/information/media-check-disable-DVD_DRIVE_GCC_T10N.fdi
[Sun Dec 23 08:26:20 2007] END HANDLER MESSAGES
[Sun Dec 23 08:26:20 2007] action exited with status 0
[Sun Dec 23 08:26:20 2007] completed event "ac_adapter AC 00000080 00000001"
[Sun Dec 23 08:26:20 2007] received event "processor CPU0 00000081 00000000"
[Sun Dec 23 08:26:20 2007] notifying client 5139[107:116]
[Sun Dec 23 08:26:20 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:20 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:20 2007] completed event "processor CPU0 00000081 00000000"
[Sun Dec 23 08:26:21 2007] received event "processor CPU1 00000081 00000000"
[Sun Dec 23 08:26:21 2007] notifying client 5139[107:116]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] completed event "processor CPU1 00000081 00000000"
[Sun Dec 23 08:26:21 2007] received event "thermal_zone THM0 00000081 00000000"
[Sun Dec 23 08:26:21 2007] notifying client 5139[107:116]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] completed event "thermal_zone THM0 00000081 00000000"
[Sun Dec 23 08:26:21 2007] received event "battery BAT0 00000080 00000001"
[Sun Dec 23 08:26:21 2007] notifying client 5139[107:116]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] notifying client 5608[0:0]
[Sun Dec 23 08:26:21 2007] executing action "/home/abatzis/Scripts/powersaving.sh"
[Sun Dec 23 08:26:21 2007] BEGIN HANDLER MESSAGES
Polling for drive /dev/hda have been disabled. The fdi file written was
  /etc/hal/fdi/information/media-check-disable-DVD_DRIVE_GCC_T10N.fdi
[Sun Dec 23 08:26:21 2007] END HANDLER MESSAGES
[Sun Dec 23 08:26:21 2007] action exited with status 0
[Sun Dec 23 08:26:21 2007] completed event "battery BAT0 00000080 00000001"
```

here's what i added to power.sh:

```
status=`awk '/^state: / { print $2 }' /proc/acpi/ac_adapter/AC/state`

case $status in
       "on-line")
                #wifi
                echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level
                #disable cd-rom polling
                hal-disable-polling --enable-polling --dev /dev/hda
                #disable uhci-hcd module
                modprobe uhci-hcd
               exit 0
       ;;
       "off-line")
                #'sched_mc_power_savings' tunable under /sys/devices/system/cpu/ controls the Multi-core related tunable. By default, this is set to '0' (for optimal performance). By
                #setting this to '1', under light load scenarios, the process load is distributed such that all the cores in a processor package are busy before distributing the
                #process  load to other processor package
                echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
                #disable wake on lan
                ethtool -s eth0 wol d
                #wifi
                echo 7 > /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level
                #disable cd-rom polling
                hal-disable-polling --dev /dev/hda
                #disable uhci-hcd module
                rmmod uhci-hcd
               exit 0
       ;;
esac

```

hope that can help someone--uchi-hcd seems to be a big power hog; loading/unloading the module saves some significant battery life (although you lose the fingerprint reader with the module unloaded).

---

### Post by David A Knight on 2007-12-26
There is no power level 7.  The settings go from 1-6.    1 being the lowest power saving mode, 5 being the highest.  6 is no power saving at all.   if you cat /sys/bus/drivers/iwl3945/*/power_level after setting it to 7 you will see that it says 6, and OFF, meaning you are getting no power saving at all.

---

### Post by mma8x on 2007-12-27
actually, there is a power level 7, which is specifically battery mode.  i assume that's max power savings.

```
cat /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level
7 (BATTERY)

```

---

### Post by David A Knight on 2007-12-29
> **mma8x said:**
> actually, there is a power level 7, which is specifically battery mode.  i assume that's max power savings.

```
cat /sys/bus/pci/drivers/iwl3945/0000\:03\:00.0/power_level
7 (BATTERY)

```

so there is, strange I wasn't seeing this before

---

