---
title: "CPU Frequency"
date: 2008-09-04
forum: Hardware
---

### Post by keroro on 2008-09-04
I can not get my notebook to run at higher CPU speeds then 800MHz.
The CPU is a Intel Core 2 Duo T8100 (2.1GHz)
Output of cpufreq-info is

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, conservative, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, conservative, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

Especially the line "frequency should be within 800 MHz and 800 MHz." seems to show the root of the problem. 
Does anybody got an idea how to change it?

---

### Post by abhinav86 on 2008-09-04
[http://DNSENQUIRY.COM](http://DNSENQUIRY.COM) is a website where you can online query about

address record of any website (A record)
ns record
whois lookup
ping domain 
ip to location
your machine ip address with location

and much more free of cost.

---

### Post by kpkeerthi on 2008-09-04
Can you post the output of ```
cat /etc/cpufreqd.conf
```

---

### Post by keroro on 2008-09-04
Here we go

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=4
#enable_remote=1
#remote_group=root
[/General]

#[acpi]
#cpid_socket=/var/run/acpid.socket
#[/acpi]

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
#[Rule]
#name=CPU Too Hot
#acpi_temperature=55-100
#cpu_interval=50-100
#profile=Performance Low
#[/Rule]

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

---

### Post by t4k1s on 2008-09-17
My T8100 seemed to be stuck at 800Mhz too, this fixed it for me:
sudo cpufreq-selector --cpu 0 -g performance
sudo cpufreq-selector --cpu 1 -g performance


For some reason, setting CPU0 only didn't work. It only appears to work when setting CPU1.

Hope this helps...

With friendly regards,
Takis

---

### Post by keroro on 2008-09-18
Thanks, Takis. Will try it later.
I tested Intrepid Ibex and it works in this version out of the box.

---

