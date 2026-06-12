---
title: "[SOLVED] Please help: ugly fix for hard disk load cycle count"
date: 2008-04-28
forum: Hardware
---

### Post by ethanay on 2008-04-28
If putting scripts in /etc/acpi/*.d do not work for you, and you have pm-utils installed, try this:

bug 59695 "hard drive killer" [comment 273]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/273") pm-utils ugly fix

check for heat issues on your laptop:
```
sudo hddtemp /dev/[x]da
```
where x = h or s depending on your drive

if you have heat problems (temp approaching 60*C) and/or absolutely need shock protection (you will be jogging w/your laptop??) then see the following to configuring your hdd for reduced i/o to actually take advantage of aggressive APM settings for head-parking and spin down:
[lesswatts.org]("http://www.lesswatts.org/tips/disks.php")
and
[Howto:improve battery life on a laptop]("http://ubuntuforums.org/showthread.php?t=729644")

Please post back with your results.  I am particularly interested whether people have found settings that reduce disk i/o acceptably.  Without suitable i/o configuration, I believe aggressive head parking and spindown settings can actually cause more power usage than they save and offer little or no shock protection because of the constant reversion to a full-power state (in addition to prematurely shortening the lifespan of the hard drive).

---

### Post by ethanay on 2008-04-28
addendum:  after resume from suspend or hibernate, the hard drive advanced power management setting returns to its default 128, despite anything that I put in the /etc/acpi/resume.d folder.

```
sudo hdparm -I /dev/sda
``` gives me the default setting until i manually re-enter ```
sudo hdparm -B 254 /dev/sda
```.

I would also LOVE to know whether anyone's figure out how to increase power efficiency and decrease disk access.  I've tried laptop-mode-tools and it doesn't seem to have any effect (even when enabling acpi support).  Other people seem to be getting results, so I figure there's something peculiar that I did.

---

### Post by ethanay on 2008-05-05
More info:

1) If you are running Hardy and
2) If you are suffering from the load cycle count for your hard disk and
3) If you have tried ugly fixes but none of them seem to make a difference then

4) check out bugs [#199094]("https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/199094") and [#89269]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/89269")

The workaround in the 2nd works for me, and I have not had problems with the load cycle count since then.

As I precaution, my apm settings (equivalent to hdparm -B XXX) in hdparm.conf, laptop-mode.conf and /etc/pm/config.d/disk all set to values of 254.  It is a mess in that there is NO indication whatsoever of which settings where take priority or are disabled under any circumstance.  If anyone has any information on this, that would be much obliged.

In the mean time, it seems that there needs to be better commenting in between the various scripts that shows their relation.  For example, "Note: when this value is set/enabled, it over-rides values in X and X" or "Note: when X is set, this value is overridden/disabled and thus can be ignored"

---

### Post by ethanay on 2008-05-12
I have figured out why none of the fixes work:  pm-utils is handling the sleep and power state functions.  It also has its own little version of laptop-mode hardware settings going when ac is unplugged.

Here are the relevant directories:
/etc/pm/*.d/ for the location of the hdparm ugly fixes
and
/usr/lib/pm-utils/*.d for the laptop-tools setting and sleep fixes

so if you are running Hardy on a clean install, there is a good chance that /etc/acpi/* has deprecated and you need to put your ugly fix scripts for the hard drive bug, and sleep bugs (unload uvcvideo) in the appropriate pm-utils locations.

see the following bug comments for more information:
[bug 59695 "hard drive killer" comment 273 pm-utils ugly fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/273")
[bug 89269]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/89269")
[bug 229693]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/229693")

note: the ugly fix -B=254 (apm disabled) is fine for me at the time because anything less causes constant clicks, which causes MORE power consumption and no bump protection.  Furthermore, install hddtemp and monitor with apm disabled.  My temp hovers around 42 C but if yours approaches 60 C then you will need to configure a more complicated power management scheme to protect your hdd from heat by using laptop-mode to cause bursty I/O in conjunction with sane hdd spindown times (hdparm -S).

---

### Post by rlogiacco on 2008-06-28
Just to be sure... my hard drive, after the ugly fix, is running about 3 parks per minute while on battery... is this value too high in your opinion?

---

### Post by ethanay on 2008-07-18
that depends...how many hours per day are you using your laptop on battery?  How many parks per day total does it amount to?  At this rate, how many days will it take for you to reach the disk's specified rated limit?

imo, 3 clicks is one per 20 seconds, which is moderate.  I was getting about 10 per minute before turning off power saving.

---

