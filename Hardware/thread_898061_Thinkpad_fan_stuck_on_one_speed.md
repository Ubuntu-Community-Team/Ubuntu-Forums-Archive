---
title: "Thinkpad fan stuck on one speed"
date: 2008-08-22
forum: Hardware
---

### Post by b.jumbo on 2008-08-22
hello.  i've got an ibm t42 thinkpad with a fan stuck at about 2600rpm.  until recently it would turn up to a higher speed when the cpu was under load and heating up.  however, recently it has stopped turning up under load and has allowed the machine to get hotter and hotter.  this behavior seems to have started around the time i updated the bios to the most recent version (that was to try to fix a revving fan problem).

i've been referring to an article on thinkwiki.org on controlling fan speed:  i've tried the tp-fancontrol application as well as sending commands to /proc/acpi/ibm/fan to turn the fan speed up. (for example: "echo level 2 > /proc/acpi/ibm/fan" ).   the result that i get (using "cat /proc/acpi/ibm/fan") shows that the change has been registered but whatever fan level value i send to the fan it keeps spinning at around 2600rpm!  (however, setting the level to zero does turn the fan off..)

would appreciate any help here. thanks!

---

### Post by xeth_delta on 2008-08-22
It seems ironic that a fix for solving... a fan speed problem should cause this...

Anyway, can the CPU frequency scale accordingly? Can you please post the contents of the /proc/acpi/fan and /proc/acpi/thermal_zone directories?

---

### Post by b.jumbo on 2008-08-22
[I]>>It seems ironic that a fix for solving... a fan speed problem should cause this...
[/I]

i agree!


i'm not sure how well the cpu frequency is scaling.  it didn't seem to last time i did a cpu intensive activity requiring 100% cpu.  maybe the temperature hadn't gotten high enough?  i cancelled the operation for fear of damaging something.    i suppose i could try it again though and see what happens..

as far as the directory contents go:

/proc/acpi/fan is empty

/proc/acpi/thermal_zone has only one directory THM0 which contains the following files and contents:

georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ ls
cooling_mode  polling_frequency  state  temperature  trip_points
georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ cat cooling_mode
<setting not supported>
georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ cat polling_frequency
<polling disabled>
georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ cat state
state:                   ok
georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ cat temperature
temperature:             46 C
georg@georg-laptop:/proc/acpi/thermal_zone/THM0$ cat trip_points
critical (S5):           93 C
passive:                 89 C: tc1=5 tc2=4 tsp=600 devices= CPU

one thought that has come to my mind is that there was other utility i had installed for a while to control fan speed (thinkpad fan control - tpfand).  it's no-longer on my system, but could it possibly have changed some settings and not reset them?

---

### Post by xeth_delta on 2008-08-23
What CPU does your computer have? Do you know the specs of your CPU and the frequencies it should be changing between, the maximum and minimum?

[EDIT]```
cat /proc/cpuinfo
```
should give you the information.

If so, you can check the idle frequency and later when running something intensive to check if it is scaling
```
cat /proc/cpuinfo
```

you can also check CPU temperature with
```
cat /proc/acpi/thermal_zone/temperature
```

what is the contents of /proc/acpi/ibm/fan?

---

### Post by b.jumbo on 2008-08-23
here are my cpu details:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.80GHz
stepping	: 6
cpu MHz		: 600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips	: 1197.00
clflush size	: 64

at around 20% cpu usage i showed 600MHz frequency (idle frequency?).

running an intensive task it went up to 1800MHz, so it seems to be scaling.

i have been checking the temp's with "cat /proc/acpi/thermal_zone/temperature".
got it up to 83deg just few minutes ago, and now it's dropped back to 55.

content of /proc/acpi/ibm/fan is:

status:		enabled
speed:		2662
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

---

### Post by xeth_delta on 2008-08-23
The temperature seems indeed a bit high and the fan should be getting faster.

Is the fan working on other operating systems? Is it possible that a new option has been added to the BIOS, to control or lock fan speed?

---

### Post by b.jumbo on 2008-08-23
i've got a barely useable version of xp installed (missing many drivers for this thinkpad) and i'm not getting much information from any hardware monitoring software on that o/s.  the fan speed seems constant as in linux, but then i haven't been able to reproduce a constant high load there either.

i've had a look around the bios and haven't found anything referring to fan speed.

---

### Post by b.jumbo on 2008-08-23
i just got the temp up to about 89deg in linux, swapped to xp and got an initial reading of 74deg.  fan speed remained the same as always...

---

### Post by xeth_delta on 2008-08-23
> **b.jumbo said:**
> i just got the temp up to about 89deg in linux, swapped to xp and got an initial reading of 74deg.  fan speed remained the same as always...

That is not good...

It seems the BIOS "update" schewed something. I would guess one of the following:
-Might be possible that there are several versions of that model, and that the update was done inadvertently for the wrong revision.
-The BIOS expects some sort of software controlling the fan speed. You mentioned you used to have some software doing that before on Linux, right?
-Bad flashing of CMOS, for some strange reason.

If none of the above, is it possible to revert to the previous BIOS version?

---

### Post by b.jumbo on 2008-08-23
hmmm..
i think first i'll try to re-apply the bios update.  

interestingly, after updating the bios last time, i was instructed to verify that the version and date after install matched the selected bios (ie. from ibm's download page).  the version did, but the date was slightly different which i thought strange but dismissed as a possible typo..

if that doesn't fix things, i'll go back to the previous bios version..

thanks, i appreciate the help so far..

---

### Post by xeth_delta on 2008-08-23
> **b.jumbo said:**
> hmmm..
i think first i'll try to re-apply the bios update.  

interestingly, after updating the bios last time, i was instructed to verify that the version and date after install matched the selected bios (ie. from ibm's download page).  the version did, but the date was slightly different which i thought strange but dismissed as a possible typo..

if that doesn't fix things, i'll go back to the previous bios version..

thanks, i appreciate the help so far..

You're welcome! Please do keep us updated.

Make sure about the computer revision. For example, an old HP laptop of mine had a model number/name, and also revision/sub-version number underneath. Laptops with different sub-version numbers were slightly different inside.

---

