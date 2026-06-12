---
title: "[Gutsy] BIOS automatic wake-up is not set using /proc/acpi/alarm"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by Fisslefink on 2007-09-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139846](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139846) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The ability to set the RTC (BIOS wakeup) alarm broke when I dist-upgraded to Gutsy.  I could really use some help with this, as I have run out of things to try (without downgrading back to Feisty)...

I wrote extensive details in my bug report, #[139846]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139846"), which I have copied below.  

Do you know what else I can try?  
Do you run Gutsy and also see this problem?
Or does it work for you?
Do you have an ASUS motherboard?
How can I systematically figure out the cause of this bug?

=== Copied directly from my bug report, #[139846 ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139846")===

Binary package hint: linux-source-2.6.22

**Ubuntu version:** Kubuntu Gutsy (development) ... last upgraded 9/16/2007
**Kernel version:** 2.6.22-11-386
**Motherboard:** ASUS P4P800E-Deluxe
**BIOS RTC Alarm Setting:** Disabled
**First broken:** This worked fine with Feisty and kernel 2.6.20-13-386. It broke upon dist-upgrading to Gutsy.

**Problem:**

I have a file on my system called /home/mythtv/timestamp that gets updated with the preferred wakeup time of the system. The contents of the file are the following:

```
$ cat /home/mythtv/timestamp
2007-09-15 09:53:59
```

The command below is issued by a script, and it copies the wakeup time to the BIOS.
```

sudo sh -c 'cat /home/mythtv/timestamp > /proc/acpi/alarm'
```

Double-checking this reveals that the time is set correctly BEFORE shutdown:
```

$ cat /proc/acpi/alarm
2007-09-15 09:26:59
```

After shutting down the computer, it does not wake at the schedule time. When it is turned back on, the day is set to '00' in /proc/acpi/alarm, as shown below:
```

$ cat /proc/acpi/alarm
2007-09-00 09:26:59
```

This is presumably the cause of the alarm failure.
[B]
Troubleshooting attempts:
[/B]
-- None of the suggestions at [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup) have worked to resolve the issue.

-- There is an interesting comment on that page under the heading *" Kernel 2.6.22+ and /sys/class/rtc/rtc0/wakealarm" *that suggests this feature broke with Kernel 2.6.22, but the proposed fix only works for Fedora Core 7 users **(Gutsy does not have the file "/sys/class/rtc/rtc0/wakealarm")**

-- A similar bug is discussed here, but my bug occurs after a full power off: [http://www.nabble.com/Real-Time-Clock-Alarm-Broken-with-2.6.22+-kernel-t4401170s15552.html](http://www.nabble.com/Real-Time-Clock-Alarm-Broken-with-2.6.22+-kernel-t4401170s15552.html) and reported here: [http://bugzilla.kernel.org/show_bug.cgi?id=899](http://bugzilla.kernel.org/show_bug.cgi?id=899)

A solution is proposed on the kernel.org bugzilla by 'rafael', but I do not have the skills needed to test it, and it sounds **hibernation-specific:**
[I]
>I think the suspend/hibernation code ordering changes after 2.6.20 are to blame
>here.
>
>Reportedly, the problem can be fixed by applying the patch from
>[http://lkml.org/lkml/2007/8/27/392](http://lkml.org/lkml/2007/8/27/392) , but that requires some other changes which
>are not present in 2.6.22.
>
>It would be nice if that could be tested on 2.6.23-rc5 with the patchset from
>[http://www.sisk.pl/kernel/hibernation_and_suspend/2.6.23-rc5/patches/](http://www.sisk.pl/kernel/hibernation_and_suspend/2.6.23-rc5/patches/) applied
>and the patch from [http://lkml.org/lkml/2007/8/27/392](http://lkml.org/lkml/2007/8/27/392) on top of it.
>
>Greetings,
>Rafael[/I]

-- MahoneyR has the same symptoms as described in this thread: [http://ubuntuforums.org/showthread.php?t=349062](http://ubuntuforums.org/showthread.php?t=349062) But the solution appears to be restarting the computer immediately after the next boot -- **this was not needed with Feisty **on my system and should not be needed now!

I'd be happy to provide more files and logs if they will help. 

==== End of bug report =====

I have a feeling this is going to be a tricky one.  Thanks for your help!

---

### Post by Fisslefink on 2007-09-25
Bump.  No one is waking up their machine with Gutsy?

---

### Post by Fisslefink on 2007-10-24
OK, I finally fixed it by formatting Gutsy, installing Feisty, and customizing MythTV to use the attached "MythWakeSet" script, and also customized /etc/init.d/hwclock.sh (attached).

My kernel is now:
```
Linux mythtvbox 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
```

The command below will now set the alarm correctly to wake up at 2007-10-24 18:18:02:
```
sudo MythWakeSet 2007-10-24 18:18:02
```

The suggestions on [http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
and [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
were very useful. 

... I am scared to update to 2.6.22 for fear it will break it again.  I hope that gets fixed soon.

---

