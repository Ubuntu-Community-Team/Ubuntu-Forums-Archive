---
title: "HDD Spindown problem solved!!"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by davebed on 2006-11-13
For those of you who have been plagued with the all-to-frequent spindown / spinup of your hard drives, I have finally found something interesting.

From all the info that I found posted in this forum on the subject, there was one important item that was missing - at least for *my* drive.

I run the Seagate ST910021AS 100GB 2.5" 7200rpm notebook drive and for some reason, **whenever HDD power management is set to _1_** **NO MATTER WHAT the spindown time is set for** the drive **ALWAYS** spins down after several seconds. I went completely mad finding this out. While I am not exactly sure what the various HDD Power Management settings will do, I found that 1=lowest (and produces the abovementioned problem) 128=some power management (currently in use and does **not** spindown the drive) and 255=no power management

Further, as I found here: [http://ubuntuforums.org/showthread.php?t=143591&page=2&highlight=spindown](http://ubuntuforums.org/showthread.php?t=143591&page=2&highlight=spindown)
The /etc/acpi/power.sh file has settings for the spindown (hdparm -S) and power management (hdparm -B) which seem to get called before those in  /etc/laptop-mode/laptop-mode.conf and so I currently use the settings in /etc/acpi/power.sh for spindown and PM (see below)

Change:
```
unction laptop_mode_enable {
$LAPTOP_MODE start

for x in /sys/bus/ide/devices/*/block; do
drive=$(basename $(readlink $x));
$HDPARM -S **[COLOR="Red"]12[/COLOR]** /dev/$drive 2>/dev/null
$HDPARM -B **[COLOR="Red"]1[/COLOR]** /dev/$drive 2>/dev/null
done

for x in /sys/bus/scsi/devices/*/block; do
drive=$(basename $(readlink $x));
$HDPARM -S **[COLOR="Red"]12[/COLOR]** /dev/$drive 2>/dev/null
$HDPARM -B **[COLOR="Red"]1[/COLOR]** /dev/$drive 2>/dev/null
done
}
```

change to 
```
unction laptop_mode_enable {
$LAPTOP_MODE start

for x in /sys/bus/ide/devices/*/block; do
drive=$(basename $(readlink $x));
$HDPARM -S [COLOR="Red"]**90**[/COLOR] /dev/$drive 2>/dev/null
$HDPARM -B [COLOR="Red"]**128**[/COLOR] /dev/$drive 2>/dev/null
done

for x in /sys/bus/scsi/devices/*/block; do
drive=$(basename $(readlink $x));
$HDPARM -S **[COLOR="Red"]90[/COLOR] **/dev/$drive 2>/dev/null
$HDPARM -B [COLOR="Red"]**128**[/COLOR] /dev/$drive 2>/dev/null
done
}
```

Note: The time set for **HDDPARM -S** is the spindown time in seconds, **multiplied by [COLOR="Red"]5[/COLOR]**, so my **90** would be 450 seconds.

Hope this helps some of you ... I've been ](*,)ing my head over it for a while.

N.B Drive spindown can have serious consequences: read [http://www.samwel.tk/laptop_mode/tools/faq.html](http://www.samwel.tk/laptop_mode/tools/faq.html)

P.S I'm interested in finding specific data for what the power management settings of 1-255 will actually control. I chose 128 arbitrarily but I'm curious what other settings might allow, without casuing me greif

---

