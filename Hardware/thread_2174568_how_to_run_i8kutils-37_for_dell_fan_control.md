---
title: "how to run i8kutils-37 for dell fan control?"
date: 2013-09-15
forum: Hardware
---

### Post by Cozze on 2013-09-15
As many ubuntu users i am struggling with a fan that is always on full speed. Launchpad now suggested a specific solution for dell laptops that needs to be installed called 'i8kutils-37'. I've downloaded the package and read the readme file but I don't understand how to install it. Can someone help me? Package can be found on [https://launchpad.net/i8kutils](https://launchpad.net/i8kutils). I think it also needs root access, but how do I get this?

Tx for helping me out, Cozze

---

### Post by vitorafsr on 2013-10-19
The easiest way is to install the ppa, and use apt-get.

sudo add-apt-repository ppa:vitorafsr/ppa
sudo apt-get update
sudo apt-get install i8kutils

After that you will need to tweak the config file "/etc/i8kmon.conf". One example is below.


# Sample i8kmon configuration file (/etc/i8kmon, ~/.i8kmon).

# Kernel I8K status file
set config(proc_i8k)    /proc/i8k

# Kernel APM status file
set config(proc_apm)    /proc/apm

# Kernel ACPI status file
set config(proc_acpi)    /proc/acpi/ac_adapter/0/status

# External program to control the fans
set config(i8kfan)    /usr/bin/i8kfan

# Applet geometry, override with --geometry option
set config(geometry)    {}

# Run as daemon, override with --daemon option
set config(daemon)    0

# Automatic fan control, override with --auto option
set config(auto)    1

# Report status on stdout, override with --verbose option
set config(verbose)    0

# Status check timeout (seconds), override with --timeout option
set config(timeout)    5

# Temperature display unit (C/F), override with --unit option
set config(unit)    C

# Temperature threshold at which the temperature is displayed in red
set config(t_high)    80

# Minimum expected fan speed
set config(min_speed)    1800

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.
set config(0)    {{- 0}  -1  55  -1  55}
set config(1)    {{- 0}  -1  55  -1  55}
set config(2)    {{- 1}  50  65  50  65}
set config(3)    {{- 2}  55 128  55 128}

# end of file

---

