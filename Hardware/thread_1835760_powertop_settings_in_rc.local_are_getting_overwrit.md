---
title: "powertop settings in rc.local are getting overwritten"
date: 2011-08-29
forum: Hardware
---

### Post by afoglia on 2011-08-29
I am trying to automatically apply the suggestions from powertop on boot.  I've installed them in /etc/rc.local, and added log messages and can see the script is setting them correctly.  But something afterwards is resetting them by the time I start up (XFCE or KDE).[*]  What could it be?

For example, in my /etc/rc.local, I execute the command

```

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

```

Yet, once I log in, I see,

```

$ cat /sys/class/scsi_host/host0/link_power_management_policy 
max_performance

```

[*] I would try going to a text console, but I'm suffering from [bug 727620]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/727620").

Here's the appropriate parts of my /etc/rc.local, and the lines from /var/log/syslog.

```

## powertop suggestions

# Increase the VM dirty writeback time from 5.00 to 15 seconds with:
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
# This wakes the disk up less frequently for background VM activity

# Enable wireless power saving mode by executing the following command:
logger "Setting wireless power timeout"
iwconfig wlan0 power timeout 500ms

# # Disable the unused bluetooth interface with the following command:
# # (causes error because bluetooth uses different module in newer Ubuntus.)
# hciconfig hci0 down ; rmmod hci_usb

# Enable SATA ALPM link power management via:
logger "Setting link power policy to min_power"
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
rslt=`cat /sys/class/scsi_host/host0/link_power_management_policy`
logger "New link power policy: ${rslt}"

# enable the power aware CPU scheduler with the following command:
logger "Enabling power aware CPU scheduler"
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
rslt=`cat /sys/devices/system/cpu/sched_mc_power_savings`
logger "Power aware CPU scheduling: ${rslt}"

# enable HD audio powersave mode by executing the following command:
logger "Enabling HD powersave mode"
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
rslt=`cat /sys/module/snd_hda_intel/parameters/power_save`
logger "HD powersave mode: ${rslt}"

exit 0

```

```

Aug 29 21:12:02 envy logger: Setting wireless power timeout
Aug 29 21:12:02 envy logger: Setting link power policy to min_power
Aug 29 21:12:02 envy logger: New link power policy: min_power
Aug 29 21:12:02 envy logger: Enabling power aware CPU scheduler
Aug 29 21:12:02 envy logger: Power aware CPU scheduling: 1
Aug 29 21:12:02 envy logger: Enabling HD powersave mode
Aug 29 21:12:02 envy logger: HD powersave mode: 1

```

(Just to be clear, I'm running natty.)

---

### Post by teeedubb on 2012-01-02
Did you happen to have any success with this? I have the same problem on x64 oneiric, the commands that are placed in /etc/rc.local have to effect. However, if I run rc.local as sudo after boot the settings are changed to what they are supposed to be. 

Its got me stumped!

---

### Post by Skylarkism on 2012-01-02
Hello,

For one reason or another, my bluetooth mouse has stopped working. This happened the day after I was looking through my powertop options. However, all the settings for powertop were reset after I restarted the computer... and the mouse had worked up until then.

The icon in the top right corner for bluetooth says that I have bluetooth enabled... but when I go to the system settings under bluetooth, the console tells me that the bluetooth is disabled. every time I try to use the slider to turn it on, it doesn't allow the slider to stay in the "on" position. Any suggestions? Thanks!!

---

