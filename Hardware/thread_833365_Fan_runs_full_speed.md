---
title: "Fan runs full speed"
date: 2008-06-18
forum: Hardware
---

### Post by Aslund on 2008-06-18
Heya all

I runned Ubuntu on my Dell Presicion M4300 fine for some time and decided now to upgrade my harddrive. But when I installed Ubuntu to the new drive I have installed U noticed that the fan runned constant all the time, soemthing that do not happen on my other harddrive. Does anyone have an idea whats wrong?

Regards

Sebastian Aslund

---

### Post by zgornel on 2008-06-19
It might be that your new hard drive gets a lot hotter than the previous one heating up the whole laptop and raising the idle CPU temperature to values where fan runs at full speed.

---

### Post by Opensource-student on 2008-06-19
I remeber reading something about this in the help files (I think) If this only happens in Ubuntu check here/search the forums.  This could also be a malfuntion in fan control settings - check your BIOS /startup settings before you load grub ect... a new hard drive *could* have changed something here.
However I think it could just be a compatabity issue with our motherboard and Ubuntu check the included help files

If you have a cramped case or a 10,000rpm drive it could kick the fan on but I dont think it would cause it to run full blast all the time

I hope this helps

---

### Post by finite9 on 2008-06-19
Could it be that the new hard drive is not entering standby mode when not in use?  Do you mean that the old hard drive went into standby mode after a certain number of minutes, but that the new drive is on constantly?  Or do you mean that the laptop fan is spinning at full speed constantly?  Are you sure it is the fault of the drive?  Have you checked the CPU frequency with cpufreq utils to make sure the CPU is going into a lower state and not running at full capacity?

If it's not entering standby you should be able to change this with hdparm.  Check out the -M and -S switches.

---

### Post by TubaTodd on 2008-06-19
> **Aslund said:**
> Heya all

I runned Ubuntu on my Dell Presicion M4300 fine for some time and decided now to upgrade my harddrive. But when I installed Ubuntu to the new drive I have installed U noticed that the fan runned constant all the time, soemthing that do not happen on my other harddrive. Does anyone have an idea whats wrong?

Regards

Sebastian Aslund

You probably want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)

```


install package: lm-sensors

run: sensors-detect
I answered "yes" to all of their questions

run: pwmconfig
to set the preferences
you can try to run fancontrol at this point as root to see if it is working.

Finally add
/usr/sbin/fancontrol &
to rc.local
```


I've kept that bookmarked in Firefox for a while. My Sony Vaio desktop runs full speed unless I follow these easy steps. 

BTW, it doesn't say in the instructions, but you MAY need to reboot before you run "pwmconfig"

---

### Post by DavidFourer on 2008-07-14
> **TubaTodd said:**
> You probably want to check out this thread.
[http://ubuntuforums.org/showthread.php?t=75972](http://ubuntuforums.org/showthread.php?t=75972)
Please help me out with fan test
My laptop recently shut down and gave overheat-warning on re-start.

I have Dell Inspiron 6000 with Intel Celeron M 1.4 GHz processor, Ubuntu 8.04, kernel 2.6.24-19-generic

I used to hear the fan clearly.  Now it's quiet; I think it's running but I'm not sure.  Don't know if some upgrade changed the fan modulation, or if some hardware broke.  Want to quickly check temperature.  Stuff at lm-sensors.org seemed over my head :confused:

This is long, but I'm going to quote the terminal output for lm-sensors
> david@davidf:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

david@davidf:~$ sudo sensors-detect
[sudo] password for david: 
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): YES
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): YES
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): YES
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 10c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x1d01
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): YES
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
david@davidf:~$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)
david@davidf:~$ 
david@davidf:~$ sudo fancontrol
Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!
david@davidf:~$ 


Thank you

---

### Post by zgornel on 2008-07-14
Try ```
cat /proc/acpi/thermal_zone/*/temperature 
``` This will report temperatures of the thermal detection devices that you have in the laptop.

---

### Post by DavidFourer on 2008-07-14
Thanks.  amazing.
shortly after starting my computer I got this sequence, which shows the temperature rising, and also something called critical temperature:
> david@davidf:~$ cat /proc/acpi/thermal_zone/*/temperature
temperature:             39 C
david@davidf:~$ 
david@davidf:~$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
<polling disabled>
state:                   ok
temperature:             46 C
critical (S5):           99 C


---

### Post by zgornel on 2008-07-14
The next step, make a ```
ls /proc/acpi/fan/*
``` If you see any directories listed means that you have fans detected. If you want to start the fans (actually each directory is associated to a speed of the fan) do
```
sudo echo "on" /proc/acpi/fan/XXXX/state
``` where "XXXX" is a directory (there may be none, one or several) name listed with the first command.

PS. If temperatures stay under 60C/80C (idle/load) you should not worry

---

### Post by DavidFourer on 2008-07-14
I have a directory called /proc/acpi/fan but it's empty
> PS. If temperatures stay under 60C/80C (idle/load) you should not worry
I'll keep that in mind.  Otherwise, I guess acpi is not controlling my fans because it doesn't detect them.

---

### Post by zgornel on 2008-07-15
> **DavidFourer said:**
> I have a directory called /proc/acpi/fan but it's empty

I'll keep that in mind.  Otherwise, I guess acpi is not controlling my fans because it doesn't detect them.

Quite so.

---

### Post by DavidFourer on 2008-07-15
re: [http://ubuntuforums.org/showthread.php?p=5383940&highlight=fan#post5383940](http://ubuntuforums.org/showthread.php?p=5383940&highlight=fan#post5383940)
> Try
cat /proc/acpi/thermal_zone/*/temperature
This will report temperatures of the thermal detection devices that you have in the laptop.
We've settled that the fan is not detected.
Another worrisom development.  "System Monitor" in "System > Administration >" menu shows cpu running much higher when computer is idle.  Used to be about 3-4 per cent.  Now 15 to 30 per cent.  I think I'm going to boot from the previous kernel (2.6.24-16-generic or something like that) untill next upgrade.

Further developments:  Using a Dell self-booting diagnostics CD, I find that the processor fan is supposed to run at 3700 rpm at high speed and detected rpm is zero rpm!  (Dell error code is 3700-011B)  I got a little help from Dell service, but without warranty, it's not worth having them repair it.  I have never opened a notebook computer case before but cleaning inside with compressed air was suggested.  Also getting newer BIOS, which does exist.  That looks like a real task, without Windows.  I don't think I'll get into that.  don't know whay it would help.

One other thing. Just for fun, how can I take the command "cat /proc/acpi/thermal_zone/*/temperature" and turn it into an app that shows the temperature or sounds alarms?  I'm not familiar with shell scripts and such.

---

