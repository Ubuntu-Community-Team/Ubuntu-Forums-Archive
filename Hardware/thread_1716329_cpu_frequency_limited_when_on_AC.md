---
title: "cpu frequency limited when on AC"
date: 2011-03-28
forum: Hardware
---

### Post by damir3004 on 2011-03-28
I am running Ubuntu 10.10 64-bit and I am having a very strange issue with my laptop (i7 720qm 1.6 GHZ).

When I am on AC (power chord plugged in), the max cpu freq is set to 1.47 GHZ and I cannot set it higher (tried different tools, e.g., cpufreq-utils, cpufreqd, powernowd). When I unplug the AC chord, it is automatically set to 1.6 GHZ and if not, I can change it to 1.6 GHZ. 

The reported cpu frequencies can be trusted as I have done some tests with Blender renderings. With 8 threads, on AC, a certain rendering finishes in 45 seconds (run multiple times). When I go on battery, the rendering finishes in 35 seconds! (so it is really running faster).

I have removed all cpu scaling utils and the problem persists. So is the problem located in the gnome-power-manager? Does this app set the cpu scaling options when I (un)plug the power chord? Does anybody have a solution to this problem?

Thanks.

---

### Post by TBABill on 2011-03-28
Something must have changed your freq scaling settings. Going to battery should automatically take you to ondemand or powersave mode (think that's what it's called). By default, ondemand should be enabled for both on AC and off AC power, and battery only should be a more conservative setting. 
 
What does the command ```
cpufreq-info
``` return?
 
I'd definiltely look into power management because you can change them from performance, conservative, etc. Are you in KDE or Gnome? I know you posted as "ubuntu" but just in case...

---

### Post by damir3004 on 2011-03-28
> **TBABill said:**
> Something must have changed your freq scaling settings. Going to battery should automatically take you to ondemand or powersave mode (think that's what it's called). By default, ondemand should be enabled for both on AC and off AC power, and battery only should be a more conservative setting. 
 
What does the command ```
cpufreq-info
``` return?
 
I'd definiltely look into power management because you can change them from performance, conservative, etc. Are you in KDE or Gnome? I know you posted as "ubuntu" but just in case...
Thanks for the quick reply.

I've installed again cpufrequtils and runned the 'cpufreq-info' command. This is the output for cpu 0 (all others are the same)
```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 933 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.47 GHz, 1.33 GHz, 1.20 GHz, 1.07 GHz, 933 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 933 MHz and 1.47 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 933 MHz.
  cpufreq stats: 1.60 GHz:26.39%, 1.60 GHz:0.00%, 1.47 GHz:66.44%, 1.33 GHz:0.00%, 1.20 GHz:0.01%, 1.07 GHz:0.03%, 933 MHz:7.13%  (27)

```You see that it is on 'ondemand' mode and between 933 Mhz and 1.47 GHz. When I unplug the powerchord it remains 'ondemand' but the range is extended to 1.6 GHz:

```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 933 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.60 GHz, 1.47 GHz, 1.33 GHz, 1.20 GHz, 1.07 GHz, 933 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 933 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 933 MHz.
  cpufreq stats: 1.60 GHz:19.27%, 1.60 GHz:0.00%, 1.47 GHz:49.09%, 1.33 GHz:0.02%, 1.20 GHz:0.06%, 1.07 GHz:0.04%, 933 MHz:31.52%  (172)

```By the way: if you wonder why 1.60 GHz is included twice in the frequency steps: that's because of rounding errors, as I see from this command:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1600000 1599000 1466000 1333000 1199000 1066000 933000 
```

So do you know how I can change the policy for the cpu range limits (when going from AC OFF to AC ON)?

BTW: I am running Gnome.

---

### Post by TBABill on 2011-03-28
I do know how to change them, but I do not know how to do so for AC versus DC independently. If you just want to run at max then you ```
sudo cpufreq-set --governor performance
```  However, from there I think you need to go into power settings to set up AC/DC settings individually and I'm not 100% sure what that does in relation to CPUFREQ settings. Perhaps some experimentation and returning to cpufreq-info will render some info?

---

### Post by TBABill on 2011-03-28
[https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling](https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling)
 
This is from Arch but goes much deeper into selections and how to set them for on AC/off AC.

---

### Post by damir3004 on 2011-03-28
It says that if you have the package 'acpid' installed (which I have), the events should be handled by[COLOR=Black] /etc/acpi/handler.sh, but I do not have that file. What I did discover is that '/etc/acpi/events/battery' and '/etc/acpi/events/ac' both call '/etc/acpi/power.sh'. The content of '/etc/acpi/power.sh':
```

#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then
    exit;
fi

pm-powersave $*

```

The content of '/usr/share/acpi-support/policy-funcs' :
```

CheckUPowerPolicy() {
    if pidof upowerd > /dev/null; then
        return 0;
    else
        return 1;
    fi
}
CheckPolicy() {
    local PMS
    PMS="gnome-power-manager kpowersave xfce4-power-manager"
    PMS="$PMS guidance-power-manager.py dalston-power-applet"
    if pidof -x $PMS > /dev/null ||
       (pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop kded kded loadedModules | grep -q klaptopdaemon) ||
       PowerDevilRunning ; then
        echo 0;
    else
        echo 1;
    fi
}

PowerDevilRunning() {
    test -x /usr/bin/dbus-send || return 1
    
    for p in $(pidof kded4); do
        test -r /proc/$p/environ || continue
        local DBUS_SESS=$(cat /proc/$p/environ | grep -z "DBUS_SESSION_BUS_ADDRESS=")
        test "$DBUS_SESS" != "" || continue
        (su - $(ps -o user= $p) -c "$DBUS_SESS dbus-send --print-reply --dest=org.kde.kded /kded org.kde.kded.loadedModules" | grep -q powerdevil) && return 0
    done
    
    return 1
}

```

Does this make sense?[COLOR=#005500][FONT=monospace][/FONT][/COLOR][/COLOR]

---

### Post by damir3004 on 2011-03-28
And running ```
sudo cpufreq-set -u 1600000 -r
``` (change the upper limit to 1.6 GHz for all cores) does not affect the range when the AC chord is plugged in, only when I unplug the AC. Strange isn't? Do you think it's a bug or am I missing something?

---

### Post by damir3004 on 2011-03-28
But even if I clear everything in '/etc/acpi/power.sh', the problem persists. So I don't think that we should look there for the problem..

---

### Post by TBABill on 2011-03-28
I'd have to lean toward the power settings somehow. It seems you have the cpufreq settings correct, and even in ondemand mode it would kick up to 1.6 under heavy load. Something else must also communicate with the governor to control how high it can go since it already shows the full range of the processor.

---

### Post by damir3004 on 2011-03-28
Found a post [here]("http://ubuntuforums.org/showthread.php?t=1077234") where the same problem is reported. The solution is to update the bios. I don't think it will help in my case as I think I already have the newest BIOS. I will try to upgrade/downgrade my BIOS and report back here.

---

### Post by damir3004 on 2011-03-28
I tried all BIOS versions, no luck.

What I now also noticed is that Turbo Boost for my i7 processor is not working (due to this issue).

When I render a Blender scene with 1 thread, only 1 cpu is active with 1.47 GHz (results found using i7z).
When I switch to battery, it is 1 cpu with 2.8 GHz (Turbo Boost is activated).

I've opened a bug report: [https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429](https://bugs.launchpad.net/ubuntu/+source/powermgmt-base/+bug/744429)

---

