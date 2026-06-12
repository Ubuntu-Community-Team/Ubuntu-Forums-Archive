---
title: "acpid Script not triggering"
date: 2010-12-04
forum: Hardware
---

### Post by agrh on 2010-12-04
I have a shell script in /etc/acpi and an event file in /etc/acpi/events, but even though the script works if run directly and the event can be seen with acpi_listen the script doesn't run with the trigger. Any ideas how I can troubleshoot this?

/etc/acpi/eepc-she.sh:

```
#!/bin/bash

if (grep -q 'discharging' /proc/acpi/battery/BAT0/state); then
    # Super Hybrid Engine On
    echo 2 > /sys/devices/platform/eeepc/cpufv

    # Disable Webcam
    echo 0 > /sys/devices/platform/eeepc/camera

    # Intel Atom N270 @ 800MHz
    echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

    # Intel GMA950 @ 200MHz
    setpci -s 00:02.0 f0.b=00,60
    setpci -s 00:02.0 f0.b=34,05

    STATUS="Enabled"
else
    # Super Hybrid Engine Off
    echo 0 > /sys/devices/platform/eeepc/cpufv

    # Webcam Off
    echo 1 > /sys/devices/platform/eeepc/camera

    # Intel Atom @ 1.60GHz
    echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

    # Intel GMA950 @ 400Mhz
    setpci -s 00:02.0 f0.b=00,60
    setpci -s 00:02.0 f0.b=33,05

    STATUS="Disabled"
fi

sleep 1
export DISPLAY=:0 && notify-send -t 1000 "Super Hybrid Engine" $STATUS
```

/etc/acpi/events/eeepc-she:

```
event=battery
action=/etc/acpi/eeepc-she.sh
```

---

### Post by conradin on 2010-12-05
show us 
```

# tail /var/log/acpid.

```

---

### Post by agrh on 2010-12-05
```
tail: cannot open `/var/log/acpid' for reading: No such file or directory
```

I looked in the conf file for acpid but couldn't find an option to turn it on, any ideas?

---

### Post by agrh on 2010-12-05
Alright, got the loggin out of /var/log/syslog:

```
Dec  5 14:03:33 andy-netbook acpid: executing action "/etc/acpi/power.sh"
Dec  5 14:03:33 andy-netbook acpid: action exited with status 0
Dec  5 14:03:33 andy-netbook acpid: executing action "/etc/acpi/eeepc-she.sh"
Dec  5 14:03:33 andy-netbook acpid: action exited with status 127
Dec  5 14:03:33 andy-netbook acpid: procfs completed event "battery BAT0 00000080 00000001"
Dec  5 14:03:33 andy-netbook acpid: procfs received event "hotkey ATKD 00000050 00000011"
Dec  5 14:03:33 andy-netbook acpid: procfs completed event "hotkey ATKD 00000050 00000011"
Dec  5 14:03:33 andy-netbook acpid: procfs received event "processor CPU0 00000081 00000000"
Dec  5 14:03:33 andy-netbook acpid: procfs completed event "processor CPU0 00000081 00000000"
Dec  5 14:03:33 andy-netbook acpid: procfs received event "processor CPU1 00000081 00000000"
Dec  5 14:03:33 andy-netbook acpid: procfs completed event "processor CPU1 00000081 00000000"

```

Does this imply I should make my script exit with '0'?

---

### Post by agrh on 2010-12-05
Turns out it is working after all :/

The problem is with notify-send not hitting my X Display, thanks for the prod to look into logging though, conradin, cheers

---

### Post by agrh on 2010-12-05
So the problem was with notify-send which must be run as the user receiving it through their DBUS session:

[PHP]#!/bin/bash

if (on_ac_power); then
    # Disable Super Hybrid Engine, Enable Webcam & Set CPU governor to ondemand
    echo 0 > /sys/devices/platform/eeepc/cpufv
    echo 1 > /sys/devices/platform/eeepc/camera
    echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    # Intel GMA950 @ 400Mhz
    setpci -s 00:02.0 f0.b=00,60
    setpci -s 00:02.0 f0.b=33,05

    STATUS="Disabled"
else
    # Enable Super Hybrid Engine, Disable Webcam & Set CPU governor to powersave
    echo 2 > /sys/devices/platform/eeepc/cpufv
    echo 0 > /sys/devices/platform/eeepc/camera
    echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    # Intel GMA950 @ 200MHz
    setpci -s 00:02.0 f0.b=00,60
    setpci -s 00:02.0 f0.b=34,05

    STATUS="Enabled"
fi

pids=`pgrep gnome-shell`

for pid in $pids; do
    # DBUS session bus for Gnome-Shell user
    DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
    /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
    # User receiving notification
    DBUS_SESSION_USERNAME=`grep -z USERNAME \
    /proc/$pid/environ | sed -e 's/USERNAME=//'`
    # Send notification
    DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS \
    su $DBUS_SESSION_USERNAME -c "notify-send -i /usr/share/icons/Faenza/apps/scalable/hardinfo.svg 'Super Hybrid Engine' '$STATUS'"
done[/PHP]

---

