---
title: "Trying to fix power management (pm-utils, acpid) on an Intel Ivy Bridge Ultrabook"
date: 2013-09-16
forum: Hardware
---

### Post by Axx83 on 2013-09-16
Hi, on my ultrabook Acer Aspire S7-391 with core i5 Ivy Bridge and Ubuntu 13.04 on I'm having issues with the power management.

The computer does not recognize when I unplug the AC cable, or more precisely the scripts of pm-utils are not run. While going from battery to AC these are run correctly

I tried to check what is not working and found that the acpi deamon throught the event /etc/acpi/events/battery
```
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh
```

runs the power.sh script
```
#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs

if [ -z "$*" ] && ( [ `CheckPolicy` = 0 ] || CheckUPowerPolicy ); then
    exit;
fi

pm-powersave $*
```

which in turns runs the pm-powersave command that recalls all the scripts in /usr/lib/pm-utils/power.d

How do see if the event battery of acpid has been run?

Thanks

---

### Post by Toz on 2013-09-16
> How do see if the event battery of acpid has been run?
Try running:
```
acpi_listen
```
...in a terminal window and then plug and unplug the battery to see whether the events are noted in the terminal window.

> which in turns runs the pm-powersave command that recalls all the scripts in /usr/lib/pm-utils/power.d
pm-utils will also run the scripts in /etc/pm/power.d (the place for user-created scripts).

> How do see if the event battery of acpid has been run?
Also have a look at the log file /var/log/pm-powersave.log. It will list the powersave scripts that are being run with each powersave execution. A good idea is to:
```
tail -f /var/log/pm-powersave.log
```
...while you are plugging/unplugging cable to get a running report.

Are you trying to run some scripts dependent on battery/ac status? If so, consider creating scripts in /etc/pm/power.d using the following template:
```

#!/bin/sh
case $1 in
    true) #laptop_mode_battery 
        # commands here
	;;
    false) #laptop_mode_ac 
        # commands here
	;;
    help) help;;
    *) exit $NA ;;
esac
exit 0
```


Reference link: [https://help.ubuntu.com/community/PowerManagement/ReducedPower]("https://help.ubuntu.com/community/PowerManagement/ReducedPower")

---

### Post by Axx83 on 2013-09-17
Hi, thanks for the help!

I first run those command and then unplug the AC cable:

acpi_listen
```
ac_adapter ACAD 00000080 00000001
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
```

tail pm-powersave
```
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_brightness false: success.
Running hook /etc/pm/power.d/xxx_notify false:

/etc/pm/power.d/xxx_notify false: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback false: success.
```

as you see I did put some scripts in etc/pm/power.d but the whole pm-powersave is not run while acpi_listen recognizes indeed that I unplug the cable!

---

### Post by Axx83 on 2013-09-17
and if I plug the cable back in:

acpi_listen
```
ac_adapter ACAD 00000080 00000001
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
ac_adapter ACAD 00000080 00000000
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
```

tail powersave
```
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_brightness false: success.
Running hook /etc/pm/power.d/xxx_notify false:

/etc/pm/power.d/xxx_notify false: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback false: success.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: success.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices true:
Setting Host Bridge 0000:00:00.0 to auto
Setting Audio device 0000:00:1b.0 to auto
Setting Wireless device 0000:02:00.0 to auto

/usr/lib/pm-utils/power.d/pci_devices true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth true:
Setting /sys/bus/usb/devices/1-1.6 to auto

/usr/lib/pm-utils/power.d/usb_bluetooth true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for wlan0 on...Done.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /etc/pm/power.d/xxx_brightness true:
**VM dirty writeback 15 seconds

/etc/pm/power.d/xxx_brightness true: success.
Running hook /etc/pm/power.d/xxx_notify true:

/etc/pm/power.d/xxx_notify true: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback true:
**VM dirty writeback 15 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback true: success.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: success.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:00.0 to on
Setting Audio device 0000:00:1b.0 to on
Setting Wireless device 0000:02:00.0 to on

/usr/lib/pm-utils/power.d/pci_devices false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA ALPM on host0 to max_performance...Done.
Setting SATA ALPM on host1 to max_performance...Done.
Setting SATA ALPM on host2 to max_performance...Done.
Setting SATA ALPM on host3 to max_performance...Done.
Setting SATA ALPM on host4 to max_performance...Done.
Setting SATA ALPM on host5 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:
Setting /sys/bus/usb/devices/1-1.6 to on

/usr/lib/pm-utils/power.d/usb_bluetooth false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Done.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /etc/pm/power.d/xxx_brightness false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_brightness false: success.
Running hook /etc/pm/power.d/xxx_notify false:

/etc/pm/power.d/xxx_notify false: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback false: success.
^C
lele@lele-Aspire-S7-391:~$ tail -f /var/log/pm-powersave.log
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_brightness false: success.
Running hook /etc/pm/power.d/xxx_notify false:

/etc/pm/power.d/xxx_notify false: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback false: success.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: success.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices true:
Setting Host Bridge 0000:00:00.0 to auto
Setting Audio device 0000:00:1b.0 to auto
Setting Wireless device 0000:02:00.0 to auto

/usr/lib/pm-utils/power.d/pci_devices true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth true:
Setting /sys/bus/usb/devices/1-1.6 to auto

/usr/lib/pm-utils/power.d/usb_bluetooth true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for wlan0 on...Done.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /etc/pm/power.d/xxx_brightness true:
**VM dirty writeback 15 seconds

/etc/pm/power.d/xxx_brightness true: success.
Running hook /etc/pm/power.d/xxx_notify true:

/etc/pm/power.d/xxx_notify true: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback true:
**VM dirty writeback 15 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback true: success.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: success.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:00.0 to on
Setting Audio device 0000:00:1b.0 to on
Setting Wireless device 0000:02:00.0 to on

/usr/lib/pm-utils/power.d/pci_devices false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA ALPM on host0 to max_performance...Done.
Setting SATA ALPM on host1 to max_performance...Done.
Setting SATA ALPM on host2 to max_performance...Done.
Setting SATA ALPM on host3 to max_performance...Done.
Setting SATA ALPM on host4 to max_performance...Done.
Setting SATA ALPM on host5 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:
Setting /sys/bus/usb/devices/1-1.6 to on

/usr/lib/pm-utils/power.d/usb_bluetooth false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Done.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /etc/pm/power.d/xxx_brightness false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_brightness false: success.
Running hook /etc/pm/power.d/xxx_notify false:

/etc/pm/power.d/xxx_notify false: success.
Running hook /etc/pm/power.d/xxx_vm_dirty_writeback false:
**VM dirty writeback 5 seconds

/etc/pm/power.d/xxx_vm_dirty_writeback false: success.
```

which means it first ran the command on true when I plugged the cable and immediately after the command with false.

---

### Post by Toz on 2013-09-17
On my laptop (as reference):
1. Unplug = ac_adapter ACPI0003:00 00000080 0000000[COLOR="#FF0000"]0[/COLOR] -> runs powersave true scenario
2. Plug = ac_adapter ACPI0003:00 00000080 0000000[COLOR="#FF0000"]1[/COLOR] -> runs powersave false scenario

On your laptop (based on your log files):
1. Unplug = ac_adapter ACAD 00000080 0000000[COLOR="#FF0000"]1[/COLOR] -> doesn't seem to run any powersave scenario
2. Plug = ac_adapter ACAD 00000080 0000000[COLOR="#FF0000"]1[/COLOR]
..............ac_adapter ACAD 00000080 0000000[COLOR="#FF0000"]0[/COLOR] -> runs false, true, false powersave scenarios in order

*Please feel free to correct the above assumptions if they are incorrect.
> **Axx83 said:**
> which means it first ran the command on true when I plugged the cable and immediately after the command with false.
According to your log files, it would appear that on insertion of the power cable, your system is registering two events:
1. plug (ac_adapter ACAD 00000080 00000001)
2. unplug (ac_adapter ACAD 00000080 00000000)
> 
acpi_listen
```
[COLOR="#FF0000"]ac_adapter ACAD 00000080 00000001[/COLOR]
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
[COLOR="#FF0000"]ac_adapter ACAD 00000080 00000000[/COLOR]
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
```
...even though your pm-powersave.log file is showing a third event (false - another plug in event).

Buth this one:
> I first run those command and then unplug the AC cable:
acpi_listen
```

[COLOR="#FF0000"]ac_adapter ACAD 00000080 00000001[/COLOR]
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
```
...doesn't make sense. If you are unplugging the cable, acpi is picking it up as a plug in event (ac_adapter ACAD 00000080 00000001). Are the events reversed?

Can you post back your dmesg log?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated?

Also, since this is a Windows 8 notebook, have you tried the **acpi_osi=\"!Windows 2012\"** kernel parameter? This parameter usually loads a different set of acpi tables based on the fact that you are not running Windows 8 (!Windows 2012). See the kernel boot parameters link in my signature for information on how to do this. Basically, the line GRUB_CMDLINE_LINUX="" in /etc/default/grub should read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
...note the escaped quotes. Once booted, post back another copy of the newly created /var/log/dmesg log file for comparison.

Otherwise, you may need to create a bug report.

---

### Post by Axx83 on 2013-09-17
Hi, thanks for the help.

I added that line to grub, updated and restarted with the cable on.

The results are exactly the same. I noticed that "Power Statistics" of Ubuntu recognizes the notebook as unplugged when it is and vice versa, just as acpi_listen reports.

I also tried to "remove" the battery by pressing the little switch on the bottom, while being on AC. These are the results

```
lele@lele-Aspire-S7-391:~$ acpi_listen
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
battery BAT0 00000080 00000001
processor CPU0 00000081 00000000
processor CPU1 00000081 00000000
processor CPU2 00000081 00000000
processor CPU3 00000081 00000000
```

the first when I press it, the second block when I release it.

this is my pastebinit
[http://paste.ubuntu.com/6120543/](http://paste.ubuntu.com/6120543/)

What else can be done? Is it a bug:

---

### Post by Toz on 2013-09-17
> **Axx83 said:**
> What else can be done? Is it a bug:
Probably. Can I have a look at your dmesg log file? Maybe there is something in there that might be helpful.

---

### Post by Axx83 on 2013-09-17
Absolutely, please go on, now I redid some tests with plug and unplug and the battery is right now DISCHARGING while the cable is in.

---

### Post by Toz on 2013-09-17
> **Axx83 said:**
> Absolutely, please go on,
Sorry, I missed the link to your dmesg file in your previous post. 

>  now I redid some tests with plug and unplug and the battery is right now DISCHARGING while the cable is in.
Are you sure the cable is a good cable? If so, it might be best to create a bug report.

---

### Post by Axx83 on 2013-09-18
The computer is brand new, the cable is original and most of all on Windows 8 works normally.

It's definitely a kernel/acpi software issue and in my opinion quite critical.

Against which packages should I report the bug?

Thanks for the support

---

### Post by Axx83 on 2013-09-18
By the way, how stable is 13.10 right now ? I'm sure there's a new kernel and acpi packages there, I might give it a try.

---

### Post by Toz on 2013-09-18
> **Axx83 said:**
> The computer is brand new, the cable is original and most of all on Windows 8 works normally.

It's definitely a kernel/acpi software issue and in my opinion quite critical.

Against which packages should I report the bug?

Thanks for the support
I would report it against acpi-support.

---

### Post by Toz on 2013-09-18
> **Axx83 said:**
> By the way, how stable is 13.10 right now ? I'm sure there's a new kernel and acpi packages there, I might give it a try.
I can't comment on the stability of 13.10 since I don't use it, however, there is an [Ubuntu+1]("http://ubuntuforums.org/forumdisplay.php?f=427") subforum here currently dedicated to that release. You might want to peruse it to get a sense. You can also boot the 13.10 cd/usb (without installing) to see if the acpi packages perform better.

---

### Post by Axx83 on 2013-09-18
> **Toz said:**
> I would report it against acpi-support.

I did both, thanks!
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/1225617](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/1225617)

---

