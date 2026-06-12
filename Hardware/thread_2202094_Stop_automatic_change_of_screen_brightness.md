---
title: "Stop automatic change of screen brightness"
date: 2014-01-27
forum: Hardware
---

### Post by mike134 on 2014-01-27
I am running Lubuntu 13.10 on an Acer TravelMate 8371 and I want to stop the brightness changing automatically on the following triggers:
[LIST=1]
[*]Plug in AC-power - currently this sets brightness to 9 (max brightness)
[*]Unplug AC-power - currently this sets brightness to 2
[*]Resume from Suspend or Hibernate - currently this sets brightness to 5
[/LIST]

I set screen brightness depending on ambient light, so I don't want it to change on any of the above triggers.  How can I disable these triggers.  I have been searching for 4 hours and haven't found anything yet as most discussions seem to be about dimming the display after certain idle time or when battery gets low or are about dimming NOT working.

I know the bios changes the fan speed (very annoying) with plugging with AC-power in and out, but it does not seems to change the screen brightness as the screen brightness does not change when I am in grub when laptop boots if I plug the AC-power in and out, so it looks to be Linux that is changing the brightness.

If I run acpi_listen, then when I unplug AC-power I see:
[FONT=courier new]# acpi_listen[/FONT][FONT=courier new]ac_adapter ADP1 00000080 00000000[/FONT]
[FONT=courier new]battery BAT0 00000081 00000001[/FONT]
[FONT=courier new]battery BAT0 00000080 00000001[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000087 00000000[/FONT]
[FONT=courier new]video DD03 00000086 00000000[/FONT]
[FONT=courier new]video DD03 00000086 00000000[/FONT]

and in /var/log/pm-powersave.log I see hooks running from /usr/lib/pm-utils/power.d

Some of the things I have tried so far are which have made not difference (light still brightens) are:
[LIST]
[*]Stopped acpid service
[*]Stopped lightdm (Light Display Manager) so just running in a terminal
[*]Disabled scripts in /usr/lib/pm-utils/power.d (by moving to a newly created "disable" directory)
[*]Looked at xfce4-power-manager, but this only has screen brightness settings for when you are inactive
[/LIST]

What process is changing the brightness and how can I stop or change this?

Thanks

Mike

---

### Post by Wolfhart on 2014-02-04
I have the same question. These automatic brightness changes in Ubuntu 13.10 are very annoying. Does anybody know how to deactivate this new feature?

Wolfhart

---

### Post by mike134 on 2014-02-07
I have solved this in part as I implemented a script to set brightness level to last saved level when laptop boots, but this script is called when resuming from suspend and hibernate too, so fixes trigger 3, but not 1 and 2 for when I unplug and plug in AC power.  Details of this script can be found at [http://ubuntuforums.org/showthread.php?t=2203403&p=12918753#post12918753](http://ubuntuforums.org/showthread.php?t=2203403&p=12918753#post12918753)

I have also found out that the brightness change does not occur on another laptop running Lubuntu 12.04, so I tried live CD for 12.04 on problem laptop and issue still occurs, so I think issue is to do with the driver for the display, as these are different:
On the Acer TravelMate 8371 laptop that has issue (brightness changes), the video card is Intel Mobile 4 Series Chipset 
On the Dell D400 laptop that is ok (does NOT change brightness), the video card is Intel 82852/855GM

Does anyone know how I can stop acpi telling graphics cards there has been a change in power, or is there an alternative driver I can use?

Thanks

Mike

---

