---
title: "[Intrepid]Resuming from suspend issues=Excessive journaling?"
date: 2009-05-10
forum: Hardware
---

### Post by ssri on 2009-05-10
Hey everyone,

I'm running Intrepid (08.10) with KDE 4.2.2, ATI Catalyst 9.3, ext3, 2.6.27-14-generic.  I've noticed that whenever I resume from suspend my laptop's harddrive is constantly reading/working, even when I closed all of my running programs before going into suspend-mode.  This renders my system slow and virtually unusable.  Furthermore, this activity lasts upwards to 7mins before I give up all hope and do a hard power off.  There is nothing too weird happening when viewing my system's activity from iotop and top.  Any running programs with excessive read/write speeds are quickly sudo killall'd.  That doesn't solve the problem though.  I do not think running apps are an issue (save firefox) since this excessive harddrive reading activity occurs even when resuming from a clean desktop.  Afterwards, when I boot in verbose mode, I notice that there is journal recovery going on.

Is this a kernel (acpi) problem, is the proprietary video driver somehow conflicting with the kernel's acpi settings or is it a hardware issue with my 5 month old laptop harddrive?

Looking forward to hearing some advice or suggestions.  Thanks!

--

---

### Post by ssri on 2009-05-21
Solved the problem after a bios update on my 6910p to F17

*crossing fingers* for now

[http://ubuntuforums.org/showthread.php?t=837275&page=2](http://ubuntuforums.org/showthread.php?t=837275&page=2)

---

### Post by ssri on 2009-05-26
> **ssri said:**
> Solved the problem after a bios update on my 6910p to F17

*crossing fingers* for now

[http://ubuntuforums.org/showthread.php?t=837275&page=2](http://ubuntuforums.org/showthread.php?t=837275&page=2)

The problem came back again.  I had a few Java programs open.  I closed the lid of my laptop and headed to the University. When I tried to resume, there was excessive journaling that wouldn't stop for 10mins until I pressed and held down power for a hard poweroff.  It seemed that the journaling mostly occurred in my home partition.  After rebooting, it seems that _plasmarc_ became corrupted, so I had to organize my desktop again.  Also, 92% of my home partition is used.  Is it the Java programs I had running, plasma suffering a crash upon resume or was it the fact that <10% of my partition was free?

---

### Post by ssri on 2009-05-26
Here's my pm-suspend.log

Initial commandline parameters: 
Tue May 26 10:39:28 PDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Tue May 26 10:39:30 PDT 2009: performing suspend
Tue May 26 11:04:09 PDT 2009: Awake.
Tue May 26 11:04:09 PDT 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/99video resume: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume: success.
/usr/lib/pm-utils/sleep.d/95packagekit resume: method return sender=:1.526 -> dest=:1.525 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume: not applicable.
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume: /usr/lib/pm-utils/sleep.d/95hdparm-apm: 50: get_power_status: not found

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
success.
/usr/lib/pm-utils/sleep.d/95anacron resume: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume: success.
/usr/lib/pm-utils/sleep.d/90clock resume: success.
/usr/lib/pm-utils/sleep.d/50modules resume: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager resume: success.
/usr/lib/pm-utils/sleep.d/05led resume: not applicable.
/usr/lib/pm-utils/sleep.d/00clear resume: success.
Tue May 26 11:04:12 PDT 2009: Finished.

---

### Post by ssri on 2009-06-11
bump

---

