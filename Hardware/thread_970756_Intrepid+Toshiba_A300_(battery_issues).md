---
title: "Intrepid+Toshiba A300 (battery issues)"
date: 2008-11-04
forum: Hardware
---

### Post by Vl@d on 2008-11-04
Ok. So i upgraded fron 8.04 and all seems to be working fine on my Toshiba A300. All except, or at least i think it's not, the laptop powersaver. 

I noticed that sometimes (mozilla, flahs-mozilla-plugins..?), the performance of my battery decrease 30m-1h. I mean, on 8.04/Debian/Xp my batteries can run over 2:55h-3:15m.. but now sometimes 'misteriously' the batteries are avilable just for 1:30-1:45m. The battery is only 1 month old so I'd discard the battery problem. I also have checked the 'reduce baklight brightness' and 'Dim display when idle' options into the power management panel(wasn't really succesful or notizable)

As i said is only sometimes so i would say that is software bug (?) 

I don't really know much about GNU-Linux related to the laptop's batteries so... Is there any report from other users with a similar laptop and similar problems that i did not see? Or any well-known bug on Intrepid about these issues?

If it can help on any way, here's the result of powertop. 

Attempt 1:

```
n                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 7.9%)         1.84 Ghz     0.0%
C0                0.0ms ( 0.0%)         1333 Mhz     0.0%
C1                0.0ms ( 0.0%)         1000 Mhz   100.0%
C2                0.5ms ( 0.8%)
C4                2.0ms (91.3%)

Wakeups-from-idle per second : 480.9    interval: 1.6s
Power usage (ACPI estimate): 18.1W (2.4 hours)

Top causes for wakeups:
  36.6% (394.0)       <interrupt> : uhci_hcd:usb1, ohci1394, mmc0, i915@pci:0000
  32.4% (349.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   9.1% ( 98.0)      <kernel IPI> : Rescheduling interrupts 
   5.3% ( 57.0)           firefox : futex_wait (hrtimer_wakeup) 
   4.6% ( 49.0)       <interrupt> : extra timer interrupt 
   4.5% ( 48.0)              Xorg : schedule_timeout (process_timeout) 

```

Attemp2:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (10.6%)         1.84 Ghz     0.0%
C0                0.0ms ( 0.0%)         1333 Mhz     0.0%
C1                0.0ms ( 0.0%)         1000 Mhz   100.0%
C2                0.5ms ( 1.0%)
C4                1.9ms (88.4%)

Wakeups-from-idle per second : 473.7    interval: 3.0s
Power usage (ACPI estimate): 18.3W (2.4 hours)

Top causes for wakeups:
  38.3% (279.0)       <interrupt> : uhci_hcd:usb1, ohci1394, mmc0, i915@pci:0000
  25.9% (189.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  10.4% ( 76.0)      <kernel IPI> : Rescheduling interrupts 
   6.6% ( 48.0)       <interrupt> : extra timer interrupt 
   6.4% ( 46.7)           firefox : futex_wait (hrtimer_wakeup) 
   5.0% ( 36.7)              Xorg : schedule_timeout (process_timeout) 


```

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 8.1%)         1.84 Ghz     0.8%
C0                0.0ms ( 0.0%)         1333 Mhz     0.0%
C1                0.0ms ( 0.0%)         1000 Mhz    99.2%
C2                0.9ms ( 1.0%)
C4                2.9ms (90.9%)

Wakeups-from-idle per second : 322.2    interval: 10.0s
Power usage (ACPI estimate): 19.2W (2.3 hours)

Top causes for wakeups:
  43.6% (216.5)       <interrupt> : uhci_hcd:usb1, ohci1394, mmc0, i915@pci:0000
  18.1% ( 90.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   9.6% ( 47.4)      <kernel IPI> : Rescheduling interrupts 
   9.1% ( 45.2)           firefox : futex_wait (hrtimer_wakeup) 
   5.6% ( 27.9)       <interrupt> : extra timer interrupt 
   2.4% ( 12.0)       <interrupt> : iwl3945 

```

Anyone can unencrypt that thing? :D By the way, powertop is giving me some tips on how optimize the performance of the battery duration. This is like: 

> Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config


Should i follow that steps or they will give me more problems than solutions?





Thanks in advance.

---

### Post by hihihi on 2009-01-04
hello, it should be no problem to try it.
powertop asks you to press U. this is quite save because IF soemthing would go wrong (printers won't connect, etc) this setting is gone after reboot.
it suggests to add this option to the grub (menu.lst), this would be a permanent solution. IF soemthing would go wrong (printers won't connect, etc) than u will have to remove this option from grub (menu.lst) and reboot.

battery-power is a thing on its own and took me quite some time to find a set of options that at the end deliver a good portion of extra time on battery (arround 30%-40% more time on my sony VAIO fz-31m)

here now a ***little HOW TO POWERSAVE ON BATTERY*:** [COLOR="black"]_[COLOR="Red"]on your own risk[/COLOR]_[/COLOR]

first of all you have to enable laptop-mode-tools, which will control the power/cpu/kernel/disk of your laptop:

Laptop Mode Tools

1)
Enable laptop-mode on battery-power:

```
	$ sudo gedit /etc/default/acpi-support
```

set line “ENABLE_LAPTOP_MODE” to “true”

```
ENABLE_LAPTOP_MODE=true
```

it will be enabled after next reboot

OR

to enable it on the fly:

	```
$ sudo laptop_mode start
```

than you should configure laptop-mode-tools, but carefully and just if u know what u are doing.
```

	$ sudo gedit /etc/laptop-mode/laptop-mode.conf
```

the most important changes i did here was to let laptop-mode-tools control the CPU in a way that it consumes less power.
laptop-mode-tools has lots of config. files and is very well documented, here some links on the topic:
[http://samwel.tk/laptop_mode/](http://samwel.tk/laptop_mode/)
[http://linux.die.net/man/8/laptop-mode.conf](http://linux.die.net/man/8/laptop-mode.conf)
more general:
[http://www.linuxjournal.com/article/7539](http://www.linuxjournal.com/article/7539)
[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)
[http://www.lesswatts.org/index.php](http://www.lesswatts.org/index.php)


2)
you could automate the suggestions displayed by powertop (most of them are very useful) like this:

Create the file /etc/udev/rules.d/80-haldisablepolling-on-batt.rules:

```
$ sudo gedit /etc/udev/rules.d/80-haldisablepolling-on-batt.rules
```

paste following lines and save:

```
# Stop hal from polling cd-drive on battery-power


ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Discharging",
RUN+="hal-disable-polling --device /dev/scd0"

ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Charging", 
RUN+="hal-disable-polling --device /dev/scd0 --enable-polling"
```

3)
Reload the UDEV rules:

```
$  sudo udevadm control –reload_rules
```

from now on it will disable cd hal-poling on battery power and enable it when on ac automatically.


similar work-around for acpi, to control the kernel usage, memory and other stuff:

4)
Create the file /etc/acpi/battery.d/30-laptopPowerSave.sh

```
$ sudo gedit /etc/acpi/battery.d/30-laptopPowerSave.sh
```

paste and save the following:

```
#! /bin/sh


## SATA link power management 

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

## VM writeback time

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

exit 0

```

5)
Create the file /etc/acpi/ac.d/30-laptopPowerUp.sh

```
$ sudo gedit /etc/acpi/ac.d/30-laptopPowerUp.sh
```

paste and save the following:

```
#! /bin/sh


## SATA link power management 

echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy

## VM writeback time

echo 500 > /proc/sys/vm/dirty_writeback_centisecs

exit 0

```

6)
Now change permissions of new files and restart the acpi-demon:

```
$ sudo chmod +x /etc/acpi/battery.d/30-laptopPowerSave.sh
$ sudo chmod +x /etc/acpi/ac.d/30-laptopPowerUp.sh
$ sudo /etc/init.d/acpid restart
```

like this the tweaks will be passed to the kernel automatically when switching to battery and will be reset to default values when switching back to ac.
those were the most important changes for me.
hope this helps you.

there are tons of other tweaks one can find on the internet, but with caution, most options are very useful and noticeable and some bring big disadvantages, like the noatime option for fstab (so i never would use nor recommend that one)

good luck!

---

