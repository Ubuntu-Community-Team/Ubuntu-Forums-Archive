---
title: "Power Consumption"
date: 2009-01-28
forum: Hardware
---

### Post by TheMemphisExperience on 2009-01-28
I'm using an ASUS F6A-X2 with a 6-cell battery. In Vista, it can last about 3 hours, maybe 4. It claims it can go over four, but real world tests do not support this claim. Under Ubuntu 8.10 64, I hit a two hour wall. If it will even hit two hours. It doesn't help that I cannot dim the screen under 8.10. 9.04 alpha3 does have this feature supported, though. 

Using powernowd or cpufreqd has not been very effective for me, but maybe I'm just doing it wrong. I'd like to know how to do it right.

Also, I'd like to know how much battery life you can squeeze out of your laptops and how much gain you can get in battery life with assorted tricks.

My gain was 50% when switching from ACER Aspire 5920 to ASUS F6a-X2. The largest gain I have experienced.

---

### Post by TheMemphisExperience on 2009-01-28
cpufreqd.conf was edited to limit processor speed to 50% on battery power. Real world tests to follow.

---

### Post by Sam Lars on 2009-01-28
I have thrown together a script with some things that are supposed to help battery life.
```
#!/bin/bash
 
# Go fast.  More or less Ubuntu defaults
if on_ac_power; then
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  mount -o remount,commit=5 /home
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 1
  echo 50 > /proc/sys/vm/swappiness
  echo 3000 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0 --enable-polling
  /etc/init.d/postfix start
  /etc/init.d/anacron start
  /etc/init.d/ntp start
  LINEBACKER=$(/tmp/backlightgot)
  xbacklight -set $LINEBACKER
else # Save power
  hdparm -B 1 -S 4 -M 128 /dev/sda
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 30000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  iwpriv wlan0 power_profile 5
  echo 10 > /proc/sys/vm/swappiness
  echo 0 > /proc/sys/vm/dirty_expire_centisecs
  hal-disable-polling --device /dev/scd0
  /etc/init.d/postfix stop
  /etc/init.d/anacron stop
  /etc/init.d/ntp stop
  /etc/init.d/rsync stop
  /etc/init.d/smartmontools stop
  xbacklight > /tmp/xbacklightgot
  xbacklight -set 30
fi
```

You may not need all of it, and some things are specific to my configuation.  Your results may vary.

You should also look at the powertop program, it's great at showing you what is causing unnecessary processor calls.

---

### Post by techdude3177 on 2009-01-28
I have a sony vaio VGN-NR160, back when i had gusty I was able to sit on battery power for about an hour to an hour and a half.  When I was beta testing 8.10, I would get about the same amount of time.  Now after some update I am only able to get 20mins out of my battery which is sad.  The info on the battery says i should be able to get 2 hours out of it.

Not really sure what to do but i am going to try a few things that are suggested here.

---

### Post by stchman on 2009-01-28
I find it surprising that you cannot dim the screen.  On my Toshiba running Hardy and Acer Aspire One running Intrepid the screen dims on battery.

---

### Post by teaker1s on 2009-01-28
laptop-mode

---

### Post by techdude3177 on 2009-01-29
I already have the computer in laptop-mode, in the power management options i made it do nothing when the battery level is critically low, it sat at 1% / 0% battery level for another 35mins if not more before the laptop died.  I parted my HD and loaded gutsy(my previous release before the 8.10 upgrade) onto it and I have success on my lifetime of my battery being extended....
not really sure where to go from here.

---

