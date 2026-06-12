---
title: "Is it safe to delete hooks/thermal?"
date: 2009-05-04
forum: Hardware
---

### Post by Olnex on 2009-05-04
Hello, my laptop has a problem, when I resume from suspend, the fan runs at full speed and never stops, I found these bug reports for the same problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343128]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343128")

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/77370]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/77370")

If I remove /usr/share/initramfs-tools/hooks/thermal, the problem seems to disappear, but is it safe to do so?

contents of thermal:

> 
#!/bin/sh

PREREQ=""

prereqs()
{
	echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
	prereqs
	exit 0
	;;
esac

# Hooks for loading thermal bits into the initramfs

. /usr/share/initramfs-tools/hook-functions

case "$DPKG_ARCH" in
# copy the right modules
powerpc|ppc64)
	# Add thermal control of Macintosh if the system is not a PS3
	if [ ! -e /sys/bus/ps3_system_bus/ ]; then
		force_load therm_pm72
		force_load windfarm_core
		force_load windfarm_cpufreq_clamp
		force_load windfarm_lm75_sensor
		force_load windfarm_max6690_sensor
		force_load windfarm_pid
		force_load windfarm_pm112
		force_load windfarm_pm81
		force_load windfarm_pm91
		force_load windfarm_smu_controls
		force_load windfarm_smu_sat
		force_load windfarm_smu_sensors
		force_load i2c-powermac
	fi
	;;
i386|amd64|ia64|lpia)
	force_load fan
	force_load thermal
	;;
esac


The first part seems to apply only to macintosh, while the second part is force loading of fan and thermal, after removing the script, I check lsmod but found no fan and thermal, I tried manually modprobe fan and thermal but does not work.

---

