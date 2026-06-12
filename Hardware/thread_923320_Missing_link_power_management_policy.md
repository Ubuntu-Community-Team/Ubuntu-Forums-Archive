---
title: "Missing link_power_management_policy"
date: 2008-09-18
forum: Hardware
---

### Post by Jens_Li on 2008-09-18
I seem to be missing my /sys/class/scsi_host/host0/link_power_management_policy.

This is whats in the directory:

```

root@jens-laptop:/sys/class/scsi_host/host0# ls -l
totalt 0
-rw-r--r-- 1 root root 4096 2008-09-18 14:00 active_mode
-r--r--r-- 1 root root 4096 2008-09-18 14:00 can_queue
-r--r--r-- 1 root root 4096 2008-09-18 14:00 cmd_per_lun
lrwxrwxrwx 1 root root    0 2008-09-18 14:00 device -> ../../../devices/pci0000:00/0000:00:1f.1/host1
-r--r--r-- 1 root root 4096 2008-09-18 14:00 host_busy
-r--r--r-- 1 root root 4096 2008-09-18 14:00 proc_name
--w------- 1 root root 4096 2008-09-18 14:00 scan
-r--r--r-- 1 root root 4096 2008-09-18 14:00 sg_tablesize
-rw-r--r-- 1 root root 4096 2008-09-18 14:00 state
lrwxrwxrwx 1 root root    0 2008-09-18 14:00 subsystem -> ../../../class/scsi_host
-rw-r--r-- 1 root root 4096 2008-09-18 14:00 supported_mode
--w------- 1 root root 4096 2008-09-18 14:00 uevent
-r--r--r-- 1 root root 4096 2008-09-18 14:00 unchecked_isa_dma
-r--r--r-- 1 root root 4096 2008-09-18 14:00 unique_id
root@jens-laptop:/sys/class/scsi_host/host0# 


```

What could be the problem, or have I missunderstood something? I want to switch this on...

Im running Ubuntu 8.04.

---

### Post by Jens_Li on 2008-09-18
And my kernel is 2.6.24-19-generic by the way, so this feature should be avalible, shouldent it?

---

### Post by Jens_Li on 2008-09-18
Thouse files just appeared. But either they were not there before or I have lost the grip of this reality.

Could it be doing the things in this guide for disk idling
[https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement") 
that made them appeare?

---

### Post by Jens_Li on 2008-09-19
Ok, those sneaky /sys/class/scsi_host/host0/link_power_management_policy blip in and out of existence. Just so people know. I was totally puzzled, thought it was me going crazy. 

I suspect it has something to do with what power savning features I switch on, but I have no idea. If anyone has more knowlege, please fill me in about what could be the cause.

Im having this script in the /etc/pm/power.d and sleep.d.

```

#!/bin/bash

#
# Script for switching between cable and battery mode. Should be run from
# /etc/pm/power.d and sleep.d
#

if on_ac_power; then
# Reset back to normal settings
  echo "On AC power."

  hal-disable-polling --enable-polling --device /dev/cdrom #Enable cd polling
  echo 0 > /sys/devices/system/cpu/sched_mc_power_savings #Processor sync savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save #Sound
  echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:05\:00.0/power_level  #Wifi saving switch off
  
  echo 1 > /proc/sys/kernel/nmi_watchdog #Vad gör denna?

  echo 0 > /proc/sys/vm/laptop_mode #Disable laplop mode
  echo 10 > /proc/sys/vm/dirty_ratio #Disable hdd savings
  echo 5 > /proc/sys/vm/dirty_background_ratio #Disable hdd savings
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs #Disable hdd savings

  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy #Disable hdd savings
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy #Disable hdd savings

#  for i in /sys/class/scsi_host/*/link_power_management_policy
#  do echo max_performance > $i
#  done

else
# Turn on aggressive power savings

  # Reducing CPU voltage scale appr appr by 35% (the XPS will however not go under 19)
#  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
#  echo "77:26 76:21 10:20 8:19 6:19 136:19" > /sys/devices/system/cpu/cpu1/cpufreq/phc_controls

  echo "On battery power."
  hal-disable-polling --device /dev/cdrom
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo 0 > /proc/sys/kernel/nmi_watchdog #Vad gör denna?
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000\:05\:00.0/power_level  #wifi power saving

  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 3000 > /proc/sys/vm/dirty_writeback_centisecs

  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy

#  for i in /sys/class/scsi_host/*/link_power_management_policy
#  do echo min_power > $i
#  done

fi

```

---

