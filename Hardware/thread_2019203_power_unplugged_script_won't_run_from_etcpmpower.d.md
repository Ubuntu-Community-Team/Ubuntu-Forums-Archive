---
title: "power unplugged script won't run from /etc/pm/power.d/"
date: 2012-07-07
forum: Hardware
---

### Post by Germanunkol on 2012-07-07
Hi,
I have created the following script and put it in /etc/pm/power.d:
```

#!/bin/sh

laptop_mode_ac() {
    xbacklight -set 80
}

laptop_mode_battery() {
    xbacklight -set 20
    echo "test" >> text.txt
}

case $1 in
    true) laptop_mode_battery ;;
    false) laptop_mode_ac ;;
    *) exit $NA ;;
esac

exit 0
```
When I run it from the command line, it changes the screen brightness just like it should.
But when I unplug the power (or plug it back in) the script doesn't seem to run....?
The line with the echo is just there to test if it runs at all, but the text.txt file is not changed.
I have used chmod +x to make it executable.
I have tried calling it different things, first "screenBrightness.sh", then I renamed it laptop-mode.sh to try and overwrite the one in /usr/lib/pm-utils

Using 12.04.

---

### Post by Toz on 2012-07-07
> **Germanunkol said:**
> Hi,
I have created the following script and put it in /etc/pm/power.d:
```

#!/bin/sh

laptop_mode_ac() {
    xbacklight -set 80
}

laptop_mode_battery() {
    xbacklight -set 20
    echo "test" >> text.txt
}

case $1 in
    true) laptop_mode_battery ;;
    false) laptop_mode_ac ;;
    *) exit $NA ;;
esac

exit 0
```
When I run it from the command line, it changes the screen brightness just like it should.
But when I unplug the power (or plug it back in) the script doesn't seem to run....?
The line with the echo is just there to test if it runs at all, but the text.txt file is not changed.
I have used chmod +x to make it executable.
I have tried calling it different things, first "screenBrightness.sh", then I renamed it laptop-mode.sh to try and overwrite the one in /usr/lib/pm-utils

Using 12.04.

When that script is run, it is run as root and it won't have access to your user X environment to be able to run xbacklight. You should consider echo a value directly into your backlight interface file. To find this interface file, look at your /sys/class/backlight directory. Hopefully you only have one directory, but if you have more than one, you'll need to find the currently active one.

The following files exist in that directory:
brightness = the file to echo the value into
actual_brightness = the current brightness value
max_brightness = the maximum value to enter

To test this as a regular user, use the following:
```
 echo <value> | sudo tee /sys/class/backlight/<interface>/brightness
```
...where <value> is the value you want to enter and <interface> is the directory name of backlight interface

Since the script is being run as root, you don't need sudo for it so use the following in your script:
```
echo value > /sys/class/backlight/<interface>/brightness
```

Here is a copy of my battery_mode script to demononstrate. Note that I do alot of other power-saving changes for when the laptop goes into battery mode:
```
#!/bin/sh
# source: https://wiki.archlinux.org/index.php/Powertop

. "${PM_FUNCTIONS}"

case $1 in
    true) #laptop_mode_battery 
	#echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	#echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
	echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
	echo 16 > /sys/class/backlight/acpi_video0/brightness
	/etc/init.d/bluetooth stop
	echo 5 > /proc/sys/vm/laptop_mode
	echo 1 > /sys/module/snd_hda_intel/parameters/power_save
	echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
	echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
	echo auto > /sys/bus/usb/devices/3-1/power/level
	;;
    false) #laptop_mode_ac 
	#echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	#echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
	echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
	echo 24 > /sys/class/backlight/acpi_video0/brightness
	/etc/init.d/bluetooth start
	echo 0 > /proc/sys/vm/laptop_mode
	echo 0 > /sys/module/snd_hda_intel/parameters/power_save
	echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
	echo 500 > /proc/sys/vm/dirty_writeback_centisecs
	echo on > /sys/bus/usb/devices/3-1/power/level
	;;
    help) help;;
    *) exit $NA ;;
esac

exit 0

```

Note the brightness adjustment being made by directly echoing a value into my backlight's interface brightness file.

---

