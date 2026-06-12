---
title: "ACPID - howto add new 'event'"
date: 2016-03-05
forum: Hardware
---

### Post by nicolasdiogo on 2016-03-05
Hello Folks,



I have a Clevo P751DM laptop, and I have installed Ubuntu 15.10 using Gnome-Shell on a 4k screen.
The above laptop has a NVidia VGA, and the usual keyboard shortcut keys to change the brightness of the screen.

I have tried to fix issue by using ACPID events to capture the keyboard shortcuts.

I identified the acpid events by logging as root in a terminal and issuing the command:
```

# acpi_listen

```

The output shows the event that is triggered by pressing the corresponding keys.

With that I have created the following event file for increasing the screen brightness (and similarly for decreasing):
```

event=video/brightnessup BRTUP 00000086 00000000
action=/etc/acpi/brightness-action.sh UP

```


The script that /etc/acpi/brightness-action.sh, is as follows:
```

#! /bin/sh
usage="the brigtness requires a parameter to change the screen brigthness; values equal to 'UP' or 'DOWN'"
STEP=5


case $1 in
				UP)
						xbacklight -inc $STEP
#						echo "INcreasing ... brigtness"
						;;
				DOWN)
						xbacklight -dec $STEP
#						echo "DEcreasing ... brigtness"
						;;
				*)
						echo $usage;;
			esac

```

The above script requires xbacklight to work.


I also attached the files, in a ZIP:
[ATTACH]267661[/ATTACH]


I was expecting the above to work after rebooting, but it fails.
The keyboard shortcuts do not change the brightness, but there is an 'icon' that displays a graphic that would imply this value changing... with a status bar increasing/decreasing at the bottom.

I would seem to indicate that somehow the event is been pickup.

While I was debugging this issue, I tried using ACPID in debug mode.
Below is the output:

```

# acpid --debug
Deprecated /proc/acpi/event was not found.  Trying netlink and the input layer...
input layer /dev/input/event0 (Power Button) opened successfully, fd 4
input layer /dev/input/event1 (Sleep Button) opened successfully, fd 5
input layer /dev/input/event10 (HDA Intel PCH Headphone) opened successfully, fd 6
input layer /dev/input/event11 (HDA NVidia HDMI/DP,pcm=3) opened successfully, fd 7
input layer /dev/input/event12 (HDA NVidia HDMI/DP,pcm=7) opened successfully, fd 8
input layer /dev/input/event13 (HDA NVidia HDMI/DP,pcm=8) opened successfully, fd 9
input layer /dev/input/event2 (Lid Switch) opened successfully, fd 10
input layer /dev/input/event3 (Power Button) opened successfully, fd 11
input layer /dev/input/event4 (AT Translated Set 2 keyboard) opened successfully, fd 12
input layer /dev/input/event5 (Video Bus) opened successfully, fd 13
input layer /dev/input/event7 (HDA Intel PCH Mic) opened successfully, fd 14
input layer /dev/input/event8 (HDA Intel PCH Line) opened successfully, fd 15
input layer /dev/input/event9 (HDA Intel PCH Line Out) opened successfully, fd 16
inotify fd: 17
inotify wd: 1
netlink opened successfully
acpid: starting up with netlink and the input layer
parsing conf file /etc/acpi/events/powerbtn
parsing conf file /etc/acpi/events/asus-wireless-off
parsing conf file /etc/acpi/events/thinkpad-cmos
parsing conf file /etc/acpi/events/asus-wireless-on
parsing conf file /etc/acpi/events/lenovo-undock
parsing conf file /etc/acpi/events/ibm-wireless
parsing conf file /etc/acpi/events/asus-keyboard-backlight-down
parsing conf file /etc/acpi/events/tosh-wireless
parsing conf file /etc/acpi/events/asus-keyboard-backlight-up
parsing conf file /etc/acpi/events/thinkpad-radiosw
parsing conf file /etc/acpi/events/brightness-down
parsing conf file /etc/acpi/events/brightness-up
acpid: 12 rules loaded
acpid: waiting for events: event logging is off
acpid: client connected from 1276[0:0]
acpid: 1 client rule loaded

```


While in debug mode the brightness is changed with the keyboard shortcuts, and the same 'icon' show the changes.
Just as it should happen.

However, when I reboot the laptop. The brightness will not work - as it does when the "acpi --debug" command is used.

As there was no error shown "acpi --debug", I would like to request some assistance on how to get these acpi event to work properly every time this laptop is rebooted.


I believed I have given sufficient information above.
Let me know what further information is needed to assist on a response to this post.


Thanks,

---

### Post by nicolasdiogo on 2016-03-21
just bumping this question - maybe a new week will clarify what is possible?

---

### Post by nicolasdiogo on 2016-04-03
bumping ...
bumping ...

---

### Post by gamberoni on 2016-09-06
Had similar issue, found this thread, and this bugreport    [https://sourceforge.net/p/acpid2/tickets/3/](https://sourceforge.net/p/acpid2/tickets/3/) that looks as your issue, and mine.

---

### Post by nicolasdiogo on 2016-09-23
thanks for the suggestion,

I am yet to understand which files i have to edit to impose the 'delay'.

could you please explain this fix?

thanks,


> **gamberoni said:**
> Had similar issue, found this thread, and this bugreport    [https://sourceforge.net/p/acpid2/tickets/3/](https://sourceforge.net/p/acpid2/tickets/3/) that looks as your issue, and mine.

---

