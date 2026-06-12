---
title: "CPU Freqency Scaling not quite working"
date: 2008-11-05
forum: Hardware
---

### Post by thedevilsjester on 2008-11-05
I followed this how to:

[http://ubuntuforums.org/showthread.php?t=21930&page=2](http://ubuntuforums.org/showthread.php?t=21930&page=2)

To setup CPU scaling, and almost everything works as it should, except that its using some 100% to 100% rule.

The info I get is:

```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 233 MHz - 1.87 GHz
  available frequency steps: 233 MHz, 467 MHz, 700 MHz, 933 MHz, 1.17 GHz, 1.40 GHz, 1.63 GHz, 1.87 GHz
  available cpufreq governors: performance
  current policy: frequency should be within 1.87 GHz and 1.87 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.87 GHz.
```

Notice the line that says: **current policy: frequency should be within 1.87 GHz and 1.87 GHz.** 

My conf file looks like:

```
# this is a comment
# see CPUFREQD.CONF(5) manpage for a complete reference
#
# Note: ondemand/conservative Profiles are disabled because
#       they are not available on many platforms.

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=0
enable_remote=1
remote_group=root
[/General]

[acpi]
acpid_socket=/var/run/acpid.socket
[/acpi]

#[nforce2_atxp1]
#vcore_path=/some/path
#vcore_default=1500
#[/nforce2_atxp1]

#[sensors_plugin]
#sensors_conf=/some/file
#[/sensors_plugin]

#[Profile]
#name=On Demand High
#minfreq=40%
#maxfreq=100%
#policy=ondemand
#[/Profile]
#
#[Profile]
#name=On Demand Low
#minfreq=20%
#maxfreq=80%
#policy=ondemand
#[/Profile]

[Profile]
name=Performance High
minfreq=100%
maxfreq=100%
policy=performance
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]

[Profile]
name=Performance Low
minfreq=80%
maxfreq=80%
policy=performance
[/Profile]

[Profile]
name=Powersave High
minfreq=60%
maxfreq=60%
policy=powersave
[/Profile]

[Profile]
name=Powersave Low
minfreq=40%
maxfreq=40%
policy=powersave
[/Profile]

#[Profile]
#name=Conservative High
#minfreq=33%
#maxfreq=100%
#policy=conservative
#[/Profile]
#
#[Profile]
#name=Conservative Low
#minfreq=0%
#maxfreq=66%
#policy=conservative
#[/Profile]

##
# Basic states
##
# when AC use performance mode
[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]
 
# stay in performance mode for the first minutes
[Rule]
name=AC Off - High Power
ac=off                   # (on/off)
battery_interval=70-100
#exec_post=echo 5 > /proc/acpi/sony/brightness
profile=Performance Low
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Medium Battery
ac=off                   # (on/off)
battery_interval=30-70
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Powersave High
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Low Battery
ac=off                   # (on/off)
battery_interval=0-30
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Powersave Low
[/Rule]

##
# Special Rules
##
# CPU Too hot!
[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

# use performance mode if I'm watching a movie
# I don't care for batteries! 
# But don't heat too much.
[Rule]
name=Movie Watcher
programs=xine,mplayer,gmplayer
battery_interval=0-100
acpi_temperature=0-60
cpu_interval=0-100
profile=Performance High
[/Rule]

```

I have a Compaq Presario C500US with a Celeron M processor, running Ubuntu 8.10.

Is there something I am missing?

When I run cpufreqd-get, I get the message: 
**No cpufreqd socket found**

---

