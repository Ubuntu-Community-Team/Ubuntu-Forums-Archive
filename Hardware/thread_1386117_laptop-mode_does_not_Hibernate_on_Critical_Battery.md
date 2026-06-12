---
title: "laptop-mode does not Hibernate on Critical Battery in Karmic"
date: 2010-01-20
forum: Hardware
---

### Post by neeraj2608 on 2010-01-20
This thread is intended to help if your computer refuses to hibernate on critically low battery (choosing instead, to cold shut down), provided:
[LIST=1]
[*] you run Ubuntu Karmic
[*] you've confirmed that changing the gnome-power-manager setting "use_time_for_policy" to "false" and configuring valid threshold values does not help (which it won't because power management in Karmic is not handled by Gnome power manager, but at least you made the effort ;)).
[*] you wish to save yourself the effort of creating a workaround by writing scripts to make the ACPI daemon poll your battery regularly and thence call the hibernate script.
[*] you've installed laptop-mode-tools and performed the requisite configurations (as outlined here: [configuring laptop-mode]("http://ubuntuforums.org/showpost.php?p=5281207&postcount=1")), noting in particular that the script [FONT="Courier New"]/etc/acpi/hibernate.sh[/FONT] works satisfactorily when invoked manually.
[*] laptop-mode is still unable to hibernate the computer when the battery is critically low (because of the problem described here: [Bug #387057: laptop-mode doesn't sense power state changes]("https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/387057")).
[/LIST]
Try to check if laptop-mode can hibernate your machine if you plug in and remove the AC adapter *after* the computer boots, and *before* the battery gets to a critical level (this is what was happening on my laptop -- an HP DV3507ea). If it does, the following solution may help:
[LIST=1]
[*]set the variable [FONT="Courier New"]ACPI_WITHOUT_AC_EVENTS[/FONT] to 1 in the file [FONT="Courier New"]laptop-mode.conf[/FONT]. The function of this variable is described in the [laptop-mode man page]("http://linux.die.net/man/8/laptop-mode.conf") as follows:
[INDENT][FONT="Courier New"]ACPI_WITHOUT_AC_EVENTS
Enable this option if you have a laptop with a buggy ACPI implementation that doesn't send out AC adapter events. Enabling this option will make laptop mode check the AC adapter state whenever the battery state changes, which achieves just about the same effect as responding to AC adapter events.[/FONT][/INDENT]
[*] set the variable [FONT="Courier New"]ENABLE_BATTERY_LEVEL_POLLING[/FONT] to 1 in the file [FONT="Courier New"]/etc/laptop-mode/conf.d/battery-level-polling.conf[/FONT].
[/LIST]
Automatic hibernation works now! =D>

HTH.

---

### Post by neeraj2608 on 2010-01-25
> **neeraj2608 said:**
> This thread is intended to help if your computer refuses to hibernate on critically low battery (choosing instead, to cold shut down), provided:
[LIST=1]
[*] you run Ubuntu Karmic
[*] you've confirmed that changing the gnome-power-manager setting "use_time_for_policy" to "false" and configuring valid threshold values does not help (which it won't because power management in Karmic is not handled by Gnome power manager, but at least you made the effort ;)).
[*] you wish to save yourself the effort of creating a workaround by writing scripts to make the ACPI daemon poll your battery regularly and thence call the hibernate script.
[*] you've installed laptop-mode-tools and performed the requisite configurations (as outlined here: [configuring laptop-mode]("http://ubuntuforums.org/showpost.php?p=5281207&postcount=1")), noting in particular that the script [FONT="Courier New"]/etc/acpi/hibernate.sh[/FONT] works satisfactorily when invoked manually.
[*] laptop-mode is still unable to hibernate the computer when the battery is critically low (because of the problem described here: [Bug #387057: laptop-mode doesn't sense power state changes]("https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/387057")).
[/LIST]
Try to check if laptop-mode can hibernate your machine if you plug in and remove the AC adapter *after* the computer boots, and *before* the battery gets to a critical level (this is what was happening on my laptop -- an HP DV3507ea). If it does, the following solution may help:
[LIST=1]
[*]set the variable [FONT="Courier New"]ACPI_WITHOUT_AC_EVENTS[/FONT] to 1 in the file [FONT="Courier New"]laptop-mode.conf[/FONT]. The function of this variable is described in the [laptop-mode man page]("http://linux.die.net/man/8/laptop-mode.conf") as follows:
[INDENT][FONT="Courier New"]ACPI_WITHOUT_AC_EVENTS
Enable this option if you have a laptop with a buggy ACPI implementation that doesn't send out AC adapter events. Enabling this option will make laptop mode check the AC adapter state whenever the battery state changes, which achieves just about the same effect as responding to AC adapter events.[/FONT][/INDENT]
[*] set the variable [FONT="Courier New"]ENABLE_BATTERY_LEVEL_POLLING[/FONT] to 1 in the file [FONT="Courier New"]/etc/laptop-mode/conf.d/battery-level-polling.conf[/FONT].
[/LIST]
Automatic hibernation works now! =D>

HTH.

Although hibernation works properly now, I've noticed that the system has become sluggish ever since I made this change. The [FONT="Courier New"]top[/FONT] command shows that when the system slows down, there are dozens of [FONT="Courier New"]laptop-mode[/FONT] processes consuming all the system resources. Strangely enough, after a brief period of time (about 2 minutes), the processes disappear automatically and the system starts responding normally again. Unfortunately, this keep repeating and eventually the system becomes so slow, the only way out is a reboot.

How my changes spawn so many instances of [FONT="Courier New"]laptop-mode[/FONT], I don't know. What's more, the problem is totally random (it doesn't start up after I start a particular application, it doesn't start a fixed amount of time after booting up, it doesn't start up only on resuming a suspended or hibernated session -- basically, I fail to see any pattern to the occurrence).

Anyway, I've decided to give up on [FONT="Courier New"]laptop-mode[/FONT] and [FONT="Courier New"]acpi-support[/FONT]. Hopefully, the Ubuntu team will manage to plug all the holes in the [FONT="Courier New"]devicekit-power[/FONT] module so I can use it "out of the box" on my HP DV3507ea.

In the meantime, I've written a simple shell script that polls the battery voltage reported by ACPI and hibernates the computer when it gets critically low. The code is given below:
```

#!/bin/sh
#-------------------------------------------------------------------------------
# Filename: /etc/acpi/battery_hibernate.sh
# Author:   Neeraj Rao
# Date:     14-Jan-2010
# File Description:
# This script is a call-back for /etc/acpi/events/hphibernate which listens to battery
# events registered by the ACPI daemon
# This script checks whether
# a. the battery is discharging and
# b. the charge capacity is at a critically low level (set to 7% of maximum capacity)
# If both these conditions are satisfied, the computer is put into hibernation
# The script prefers to use the acpitool utility if it is available
#-------------------------------------------------------------------------------

if [[ -a `which acpitool` ]]; then
  NOTIFY_MARGIN=10;    #10% of total capacity of 4554 mAh.
  SAFE_MARGIN=7;       #7% of total capacity of 4554 mAh. We hardcode the value
                       #as a percentage here because acpitool is good enough to
		       #report it directly
  if [[ -n `acpitool | grep -oh 'off-line'` ]]; then
    current_capacity=`acpitool | grep -oh charg.*$  | grep -oe '[.0-9]*'`;
    if ((`echo "$current_capacity < $NOTIFY_MARGIN" | bc` && `echo "$current_capacity > $SAFE_MARGIN" | bc`)); then
      export DISPLAY=:0 && export XAUTHORITY=/home/<user_name>/.Xauthority && su <user_name> -c 'notify-send -u critical -t 3000 -i gtk-dialog-warning "Warning" "
      Your battery is critically low.
      Please insert an AC Adapter at once."' #export DISPLAY and Xauthority to avoid DBUS session errors
                                             #See http://cweiske.de/tagebuch/DBus%20notify-send%20over%20network.htm
    fi
    if ((`echo "$current_capacity < $SAFE_MARGIN" | bc`)); then
      export DISPLAY=:0 && export XAUTHORITY=/home/<user_name>/.Xauthority && su <user_name> -c 'gnome-screensaver-command -l' #lock screen first
      sudo /usr/sbin/pm-hibernate
    fi
  fi

elif (grep -q 'charging state:          discharging' /proc/acpi/battery/BAT0/state); then
  SAFE_MARGIN=`grep -oh 'last full.*$' /proc/acpi/battery/BAT0/* | grep -oe '[0-9]*'`;
  NOTIFY_MARGIN=`echo "0.1*$SAFE_MARGIN" | bc`; #10% of total capacity of 4554 mAh. We must calculate
  SAFE_MARGIN=`echo "0.07*$SAFE_MARGIN" | bc`;  #7% of total capacity of 4554 mAh. We must calculate
                                                #the value in terms of battery capacity (mAh)
					        #because /proc/acpi/battery/BAT0/state
					        #does not report the present capacity of the battery
					        #as a percentage

  current_capacity=`grep -oh remaining.*$ /proc/acpi/battery/BAT0/* | grep -oe '[0-9]*'`;
  if ((`echo "$current_capacity < $NOTIFY_MARGIN" | bc` && `echo "$current_capacity > $SAFE_MARGIN" | bc`)); then
    export DISPLAY=:0 && export XAUTHORITY=/home/<user_name>/.Xauthority && su <user_name> -c 'notify-send -u critical -t 3000 -i gtk-dialog-warning "Warning" "
    Your battery is critically low.
    Please insert an AC Adapter at once."' #export DISPLAY and Xauthority to avoid DBUS session errors
                                           #See http://cweiske.de/tagebuch/DBus%20notify-send%20over%20network.htm
  fi
  if ((`echo "$current_capacity < $SAFE_MARGIN" | bc`)); then
    export DISPLAY=:0 && export XAUTHORITY=/home/<user_name>/.Xauthority && su <user_name> -c 'gnome-screensaver-command -l' #lock screen first
    sudo /usr/sbin/pm-hibernate
  fi
fi

#-------------------------------------------------------------------------------
# End of File
#-------------------------------------------------------------------------------

```
This script is to be placed in [FONT="Courier New"]/etc/acpi[/FONT]. You can call it whatever you want; I've named it [FONT="Courier New"]battery_hibernate.sh[/FONT].
Make sure the script is executable. 
You must replace [FONT="Courier New"]<user_name>[/FONT] by your user id.

The listener script to register our hibernation script as a handler for the ACPI battery event is to be placed in /etc/acpi/events (you can call it whatever you want; the "action" variable specifies the callback script and should have the same filename as our hibernation script):
```

event=battery.*
action=/etc/acpi/battery_hibernate.sh

```

---

### Post by Person_1873 on 2010-02-27
just as a quick question, does that second script require being made executable? and does it require a shell environment stated at the top?

---

### Post by neeraj2608 on 2010-02-27
> **Person_1873 said:**
> just as a quick question, does that second script require being made executable? and does it require a shell environment stated at the top?

No to both questions.

---

### Post by SecretCode on 2010-03-24
> **neeraj2608 said:**
> 
[LIST=1]
[*] ...
[*] ... (which it won't because **power management in Karmic is not handled by Gnome power manager**, but at least you made the effort ;)).
[/LIST]


Why do you say this? If you are claiming that it's true, please provide a reference. 

imho power management in Karmic **is** handled by gnome-power-manager (although it may have bugs).

---

