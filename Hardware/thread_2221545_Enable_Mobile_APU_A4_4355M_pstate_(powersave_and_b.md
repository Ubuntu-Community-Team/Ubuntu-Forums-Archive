---
title: "Enable Mobile APU A4 4355M pstate (powersave and boost mode) and tweak it!"
date: 2014-05-02
forum: Hardware
---

### Post by mr-fabio90 on 2014-05-02
Hi everybody

after so many troubles with my computer and ubuntu (Samsung 535u3c A03) since 12.04 version, now on 14.04 i can say i'm happy!:D
The real still existing problem is power management and power consumption with those APUs on 80% battery(86.9% remaning capacity), wifi enabled, i've more o less 3..3.30h now!(2.30 before tweak).
So here's how to do the tweak.

By default..i suppose..pstate 6 with 900Mhz frequency(0.1500 vcore) is disabled so that your lowest profile is 1300Mhz one.
 1) Download [Turion Power Control]("https://code.google.com/p/turionpowercontrol/")
 2) Run " sudo modprobe cpuid " and " sudo modprobe msr "
 3) cd your directory and run " sudo ./TurionPowerControl -l " to verify your cpu active states and frequencies
 4) Your pstate 6 should have flag En:0 (disabled)
 5) Run " sudo ./TurionPowerControl -en 6 " to enable it
 6) Now you have to reboot and repeat step 1 (you should see 0.9 freq in your indicator-cpufreq on unity)
 7) Let's undervolt pstate 6 to save more power. Run " sudo ./TurionPowerControl -set pstate 6 vcore 0.1000 "
 8) Now if you repeat step 3 you should see your pstate 6 enabled and at 0.1000 vcore

Now we have to enable boost pstates and set everything to start on boot.
 9) Run " sudo ./TurionPowerControl -boostenabled "
 10) Run " sudo gedit /etc/rc.local"
 11) Add before "exit 0" those commands
[LIST]
[*]sudo modprobe cpuid 
[*]sudo modprobe msr 
[*]cd your TurionPowerControl directory 
[*]sudo ./TurionPowerControl -boostenabled 
[/LIST]
 12) Save the file and reboot! DONE!

Now you should have your APU fully working an setted to save energy..while using pstate6 profile ("power saving profile").
Good Luck to everyone ;););)[COLOR=#ff0000]

!!!!!!!!!IMPORTANT UPDATE!!!!![/COLOR]
I found that after powering off the computer, the APU restore it's default settings.
I'm actually working on it!!!!
STAY TUNED!!

[COLOR=#ff0000]!!!!!!!!IMPORTANT UPDATE 2!!!!!!![/COLOR]
Ok actually the only way to make it work is to repeat steps 5 & 7 and reboot!
Every time you'll power off your computer you loose pstate6(but not the boosted states)!
So everytime you start you pc just repeat steps 5 and 7 and reboot to have all setted!

---

### Post by e-San on 2014-07-20
Awesome!

Many thanks for sharing this. It does work and seems to be stable. 
Did You try to undervoltage other pstates?

Also, i suggest to (build and) copy TurionPowerControl binary to /bin directory so we do not need to cd. I also symlinked it to /bin/tpc so my commands look like:
sudo tpc -boostenabled

**edit**.
is it possible to get over 1900 MHz?
I enabled boost, and tpc claims it is enabled but after overloading [FONT=courier new]stress[/FONT] on my maximum freq for CPU is 1900.
i'm using tlp to control all this stuff and here is part of config file:

```
# Select a cpu frequency scaling governor: ondemand/powersave/performance/conservative
# Important:
# - You *must* disable your distribution's governor settings or conflicts will occur
# - ondemand is sufficient for *almost all* workloads, you should know what you're doing!
CPU_SCALING_GOVERNOR_ON_AC=conservative
CPU_SCALING_GOVERNOR_ON_BAT=powersave

# Set the min/max frequency available for the scaling governor.
# Possible values strongly depend on your cpu. For available frequencies see
# tlp-stat output, Section "+++ Processor".
# Hint: Parameters are disabled by default, remove the leading # to enable them,
#       otherwise kernel default values are used.
CPU_SCALING_MIN_FREQ_ON_AC=900
CPU_SCALING_MAX_FREQ_ON_AC=2400
CPU_SCALING_MIN_FREQ_ON_BAT=900
CPU_SCALING_MAX_FREQ_ON_BAT=1300

# Set the cpu "turbo boost" feature: 0=disable / 1=allow
# Requires an Intel Core i processor and kernel 3.7 or later.
# Important:
# - This may conflict with your distribution's governor settings
# - A value of 1 does *not* activate boosting, it just allows it
CPU_BOOST_ON_AC=1
CPU_BOOST_ON_BAT=0
```

**edit2**. 
do You know how to werify if boost is enabled?
[I]cat /sys/devices/system/cpu/cpufreq/boost 
[/I]says it is not. so i need to *echo 1 > cat /sys/devices/system/cpu/cpufreq/boost *

Best regards!

---

### Post by e-San on 2014-07-22
my current rc.local:

```
san@sammie:~ > cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#Testing:
#echo N>/sys/module/drm_kms_helper/parameters/poll

#Radeon Dynamic Power Manager applet
chmod a+w /sys/class/drm/card0/device/power_dpm_force_performance_level
chmod a+w /sys/class/drm/card0/device/power_dpm_state

#Turion Power Control
modprobe cpuid
modprobe msr
tpc -boostenable

#TPC for CPU powersave
tpc -en 6

tpc -set pstate 2 vcore 0.0750  #0.0500 - unstable      #0.0750 #0.1125 #0.1625 #0.2125
tpc -set pstate 3 vcore 0.0625                                  #0.0750 #0.1125 #0.1625
tpc -set pstate 4 vcore 0.0625  #0.0375 - unstable?     #0.0500 #0.0750 #0.1125
tpc -set pstate 5 vcore 0.0500                          #0.0750
tpc -set pstate 6 vcore 0.0500  #0.0250 - unstable      #0.0500 #0.0500

#tpc -set pstate 2 vcore 0.0500 #kernel machine check failed
#tpc -set pstate 6 vcore 0.0125 #unstable
#tpc -set pstate 6 vcore 0.0250 #unstable

#tpc -rampuptime 8
#tpc -rampdowntime 12

#Max CPU speed (ac and bat!)
#echo 1300000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
#echo 1300000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq

#It seems that `tpc -boostenable` does NOT work
echo 1 > /sys/devices/system/cpu/cpufreq/boost

#TLP
#service tlp stop
#service tlp start

exit 0
```

All voltages are rised up by one step for security.
But i'm not sure if there is any real improvement =/

---

### Post by e-San on 2014-07-23
Ok, i tested those setting and it WAS wrong.
While using mprime -t, i've found out that pc reboots when 1900MHz is set to 0.0750. I checked all others and my tpc -l output looks now like this:

```
core 0 pstate 0 (pb0) - Boost PState Disabledcore 0 pstate 1 (pb1) - Boost PState Disabled
core 0 pstate 2 (p0) - En:1 VID:117 FID:3 DID:0.00 Freq:1900 VCore:0.0875
core 0 pstate 3 (p1) - En:1 VID:118 FID:18 DID:1.00 Freq:1700 VCore:0.0750
core 0 pstate 4 (p2) - En:1 VID:120 FID:14 DID:1.00 Freq:1500 VCore:0.0500
core 0 pstate 5 (p3) - En:1 VID:120 FID:10 DID:1.00 Freq:1300 VCore:0.0500
core 0 pstate 6 (p4) - En:1 VID:121 FID:2 DID:1.00 Freq:900 VCore:0.0375
```

Didn't test p5 at 0.0375V. Maybe i'll do it later.
My CPU at 900MHz while testing for few minutes gets temperature of about 62C.
It looks like it won't get hotter than 75C at full load - it is lower than usual at normal (but heavy) work (80C).

[B]edit.
[/B]since we are unable to test if cpu works on boost mode with our voltage, i set it to 0.2000

---

