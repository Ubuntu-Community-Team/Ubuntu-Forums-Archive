---
title: "Problem with KLaptop : changing powered status does not change power profile"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by ElectricCoyote on 2006-08-24
Hi, I'm using Kubuntu and the Klaptop kicker utility on my Thinkpad T40p.  
I have my default power profiles set up such that not powered will switch the 
system performance profile to "ondemand" and powered will change the system 
performance profile to "performance".  However, when I plug and unplug the 
laptop, the system performance profile does not change.

Now, if I log out and log back in, Klaptop senses the current state and
updates the profile.  If I quit Klaptop and restart it, this also happens.
In short, if I do anything to KLaptop which causes it to notice that things
have changed, then it adjusts the profile correctly.  It just won't do it
automatically.

KLaptop does change the icon from powered to battery when I plug and unplug
AC.  So that much seems to be working.  I have clicked the "Setup Helper
Application" in the "ACPI Config" tab of Klaptop's control panel.  
Suspend works fine.  I have all of the other checkboxes selected there as 
well.  I'm really not sure what else I should be looking for.

How do I get KLaptop to automatically change the power profile when I
change from AC to battery?

Here's what spews in my /var/log/acpi when I unplug the power cable:

```
[Thu Aug 24 21:49:24 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:24 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:24 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:24 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] action exited with status 0
[Thu Aug 24 21:49:24 2006] completed event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:24 2006] received event "ac_adapter AC 00000080 00000000"
[Thu Aug 24 21:49:24 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:24 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:24 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] action exited with status 0
[Thu Aug 24 21:49:24 2006] completed event "ac_adapter AC 00000080 00000000"
[Thu Aug 24 21:49:24 2006] received event "processor CPU 00000080 00000000"
[Thu Aug 24 21:49:24 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:24 2006] completed event "processor CPU 00000080 00000000"
[Thu Aug 24 21:49:24 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:24 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:24 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:24 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:24 2006] action exited with status 0
[Thu Aug 24 21:49:24 2006] completed event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:24 2006] received event "processor CPU 00000081 00000000"
[Thu Aug 24 21:49:24 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:24 2006] completed event "processor CPU 00000081 00000000"
Laptop mode enabled, active.

```

Here's what appears when I plug the AC back in:

```
[Thu Aug 24 21:49:32 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:32 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:32 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:32 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:32 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:32 2006] action exited with status 0
[Thu Aug 24 21:49:32 2006] completed event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:32 2006] received event "ac_adapter AC 00000080 00000001"
[Thu Aug 24 21:49:32 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:32 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:32 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:32 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:32 2006] action exited with status 0
[Thu Aug 24 21:49:32 2006] completed event "ac_adapter AC 00000080 00000001"
[Thu Aug 24 21:49:32 2006] received event "processor CPU 00000080 00000000"
[Thu Aug 24 21:49:32 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:32 2006] completed event "processor CPU 00000080 00000000"
[Thu Aug 24 21:49:32 2006] received event "processor CPU 00000081 00000000"
[Thu Aug 24 21:49:32 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:32 2006] completed event "processor CPU 00000081 00000000"
[Thu Aug 24 21:49:35 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 24 21:49:35 2006] notifying client 4453[108:108]
[Thu Aug 24 21:49:35 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 24 21:49:35 2006] BEGIN HANDLER MESSAGES
[Thu Aug 24 21:49:35 2006] END HANDLER MESSAGES
[Thu Aug 24 21:49:35 2006] action exited with status 0
[Thu Aug 24 21:49:35 2006] completed event "battery BAT0 00000080 00000001"
Laptop mode enabled, not active.

```

Anybody also see this problem?

---

### Post by ElectricCoyote on 2006-08-25
Hi again, after thinking about the problem a little bit, I decided to
manually insert the change of power profile into the /etc/acpi/power.sh
script file.  Here's what my file looks like now:

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start

    for x in /sys/bus/ide/devices/*/block; do
        drive=$(basename $(readlink $x));
        $HDPARM -S 12 /dev/$drive 2>/dev/null
        $HDPARM -B 1 /dev/$drive 2>/dev/null
    done

    for x in /sys/bus/scsi/devices/*/block; do
        drive=$(basename $(readlink $x));
        $HDPARM -S 12 /dev/$drive 2>/dev/null
        $HDPARM -B 1 /dev/$drive 2>/dev/null
    done
    /bin/echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do
        drive=$(basename $(readlink $x));
        $HDPARM -S 0 /dev/$drive 2>/dev/null
        $HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do
        drive=$(basename $(readlink $x));
        $HDPARM -S 0 /dev/$drive 2>/dev/null
        $HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
    /bin/echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then
        for SCRIPT in /etc/acpi/battery.d/*.sh; do
            . $SCRIPT
        done
        if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
            (sleep 5 && laptop_mode_enable)&
        fi
    else
        for SCRIPT in /etc/acpi/ac.d/*.sh; do
            . $SCRIPT
        done
        if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
            (sleep 5 && laptop_mode_disable)&
        fi
    fi

```

Note where I've inserted the lines to change the power management scheme
in the /sys/*/scaling_governor entries.

I shouldn't have to hack it this way though.  Do people have positive
experiences with KLaptop and having it automatically change their
power profile when they connect or disconnect the AC adaptor?

Does anyone actually know how KLaptop monitors this or should monitor it?
I'm tempted (in my copious spare time of course) to look at the source
to see if I can determine how it works...  Any advice would be greatly
appreciated.

The other possibility is that there exists some other program/package
that I'm not aware of which is blocking KLaptop from changing the 
profile...

---

### Post by Melcar on 2006-08-25
I'm running Kubuntu also and I have noticed the same thing.  Not that hard to manually change the profiles.  Annoying but not earth shattering.  Still better than Ubuntu and it's lack of power saving features (you have to download them yourself).

---

### Post by ElectricCoyote on 2006-08-25
> **Melcar said:**
> I'm running Kubuntu also and I have noticed the same thing.  Not that hard to manually change the profiles.  Annoying but not earth shattering.  Still better than Ubuntu and it's lack of power saving features (you have to download them yourself).

Hi Melcar. Yes, I completely agree with you. It's not a dealbreaker at all.
I LOVE Kubuntu with acpi support working on my t40p. However, having
upgraded from Debian, where I used apm with cpufreq which did switch my
cpu clockspeed when I switched from AC power to battery, it's a little bit 
of a downer to see that this wasn't also automatic on Kbuntu.

In any case, maybe this can serve as a feature request for future versions
of KLaptop?  I wonder if the maintainer will see this request...

---

