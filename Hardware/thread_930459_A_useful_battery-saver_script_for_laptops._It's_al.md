---
title: "A useful battery-saver script for laptops. It's almost done but I need some help !"
date: 2008-09-26
forum: Hardware
---

### Post by Axx83 on 2008-09-26
Hello everyone, I'm an happy owner of a thinkpad x60s (splendid piece of hardware) what I've been trying to do in the past weeks is to create the definitive power saving script that runs automatically when I switch to and from battery.

This script is to be considered good only for notebooks with this configuration:
Intel CPU
Intel motherboard chip
Intel graphics card
Intel wireless card
Actually this is quite common, probably the most common configuration these days, but check it before installing this script.

These are the steps I've accomplished, later I'm gonna post some questions:

These tips where collected from the website lesswats.org, from using intel's powertop and of course through this forum:

1 - Create the script
```
sudo gedit 99-save_power.sh
```
Now put this code inside the script
```
#!/bin/bash

# on ac power
if on_ac_power; then
echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
echo 0 > /proc/sys/vm/laptop_mode
echo 10 > /proc/sys/vm/dirty_ratio
echo 5 > /proc/sys/vm/dirty_background_ratio
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
echo 100 > /proc/acpi/video/VID/LCD0/brightness
echo 100 > /proc/acpi/video/VID1/LCD0/brightness
echo 6 > /sys/bus/pci/drivers/iwl3945/*/power_level

# on battery power
else
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 5 > /proc/sys/vm/laptop_mode
echo 40 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 50 > /proc/acpi/video/VID/LCD0/brightness
echo 50 > /proc/acpi/video/VID1/LCD0/brightness
echo 3 > /sys/bus/pci/drivers/iwl3945/*/power_level
fi
```
The first block is run when on ac power and the second when on battery.

The value '3' for iwl3945 is not the least consuming one, but it's a good compromise for those of us that have an older router. '5' would be the best, maybe when I buy a new device...

I've also disabled gnome-power-manager in managing backlight, with thinkpads it just doesn't work, with this sys interface it works perfectly. Put 40 or 30 in place of 50 if you can stand very dark screens, you will probably reach 10 watt this way.

Edit laptop mode config file, it's not a good idea to let it handle the hard drive, search the forum for more info tough.

Now let's make the script runnable
```
chmod +x 99-save_power.sh
```

2 - Install the script
```
sudo install 99-save_power.sh /etc/acpi/ac.d
sudo install 99-save_power.sh /etc/acpi/battery.d
sudo install 99-save_power.sh /etc/pm/power.d
sudo install 99-save_power.sh /etc/pm/sleep.d
```

3 - Test the script
Just go from Ac to battery, run powertop (sudo powertop) and you'll see that 1st you have used all it's tips and 2nd you use 2 or 3 less watts than before.

4 - Other tips
Remove the usb1 module when on battery. This is useful to a lot of laptops that have problem with uhci module. Since it's used just for usb1 peripherals you can disable it when on battery:
```
sudo modprobe -Q -r uhci_hcd
```
to turn it on again:
```
sudo modprobe -Q uhci_hcd
```
My Thinkpad spares at least 3 watts without this. Amazing.

5 - QUESTIONS

#1
These is one command that my script runs but powertop doesn't recognize:
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
it asks me for it everytime I run it, then I press S and it shuts up. But when I close and restart powertop it suggests me the same command !
This problem does NOT occur with my Acer Travelmate.

Thanks for the patience, you'll be rewarded.

---

### Post by Thingymebob on 2008-09-27
Have a look at [http://www.lesswatts.org]("http://www.lesswatts.org") for a few others to add

I went about this slightly differently and changed the /etc/acpi/power.sh, /etc/default/acpi-support (in this one enable laptop mode is disabled and needs to be enabled)

so my /etc/acpi/power.sh now looks like:
```

#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S $SPINDOWN_TIME /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done

 echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
 echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
 echo 5 > /proc/sys/vm/laptop_mode
 mount -o remount,noatime /
 mount -o remount,noatime /home
 mount -o remount,noatime /boot
 xset dpms 0 0 120
 echo 10 > /sys/module/snd_hda_intel/parameters/power_save
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block*; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
 
 echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
 echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
 echo 0 > /proc/sys/vm/laptop_mode
 mount -o remount,relatime /
 mount -o remount,relatime /home
 mount -o remount,relatime /boot
 xset dpms 0 0 600
 echo 0 > /sys/module/snd_hda_intel/parameters/power_save

}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done

```

no need to write / install any additional scripts BTW Let gnome-power-manager control the backlight.

---

### Post by Axx83 on 2008-09-27
> **Thingymebob said:**
> others to add

set the wireless interface to the max powersaving
```
iwpriv [eth1] set_power 5 
```
where [eth1] is the wireless interface (set_power 6) would set the default back (power saving disabled)

I sort of understood from lesswats that with my driver, iwl3945, the powersaving function is sort of automatized in the kernel and the set power fuction is less useful.

But thanks anyway, I'll try it immediately and check if it works \\:D/

---

### Post by Thingymebob on 2008-09-27
Also in gconf-editor
Apps>gnome-power-manager>backlight to control the backlight
Apps>gnome-power-manager>cpufreq to set how aggressive frequency scaling is
(lower=greater cpu use before up scaling the frequency)
I also set the governor (policy_battery) to powersave  and (policy_ac) to ondemand

---

### Post by Axx83 on 2008-09-27
> **Thingymebob said:**
> Also in gconf-editor
Apps>gnome-power-manager>backlight to control the backlight
Apps>gnome-power-manager>cpufreq to set how aggressive frequency scaling is
(lower=greater cpu use before up scaling the frequency)
I also set the governor (policy_battery) to powersave  and (policy_ac) to ondemand

For the backlight, as I mentioned before, gnome power manager is not too good at managing it (like almost all it does) and I switched it off, now I use a button on the screen with the xbacklight command, BUT I'm trying to get it automatic when I pulg and unplug ac. Not succedeed so far.

Regarding the governor, I read in the forum that ondemand is the best for both ac and battery, because it comsumes less going from low power to high power to perform a task than doing them all on low power, besides the fact that it's overall slower.

---

### Post by Thingymebob on 2008-09-27
> **Axx83 said:**
> For the backlight, as I mentioned before, gnome power manager is not too good at managing it (like almost all it does) and I switched it off, now I use a button on the screen with the xbacklight command, BUT I'm trying to get it automatic when I pulg and unplug ac. Not succedeed so far. Sorry missed that

> 
Regarding the governor, I read in the forum that ondemand is the best for both ac and battery, because it comsumes less going from low power to high power to perform a task than doing them all on low power, besides the fact that it's overall slower.You're right here, changed mine.

---

### Post by Axx83 on 2008-09-27
> **Thingymebob said:**
> Sorry missed that

You're right here, changed mine.

No problem, I'm happy that someone reads this topic, the more the better, I just hope to find the PERFECT script for battery management to help anyone get a little more than 1 hour out of their laptops !

So far with my thinkpad x60s I can squeeze 2 hours 30 minutes with all these tips, definitely not bad. In windows tough it's close to 3 hours and 10 minutes...

---

### Post by Thingymebob on 2008-09-27
If i do xbacklight -set (anything) in a terminal I'm getting *"No outputs have backlight property"*
so I'm now poking around to find out how gnome power manager is doing it

---

### Post by squaregoldfish on 2008-09-27
I've been using the file /proc/acpi/video/VID/LCD/brightness.

cat the file to see what your options are, and echo the value you want into the file.

Steve.

---

### Post by Axx83 on 2008-09-27
> **squaregoldfish said:**
> I've been using the file /proc/acpi/video/VID/LCD/brightness.

cat the file to see what your options are, and echo the value you want into the file.

Steve.

mmm I just tried this way but I didn't understand something:
I got 2 vid under acpi/video
```
root@myname-laptop:/home/myname# cat /proc/acpi/video/VID/LCD0/brightnesslevels:  100 30 30 40 50 60 70 80 90 100
current: 100
root@myname-laptop:/home/myname# cat /proc/acpi/video/VID1/LCD0/brightness
levels:  100 30 30 40 50 60 70 80 90 100
current: 100
```
but both works when I echo 50 them, the brightness goes down.
Which one should I use ? Maybe both ?
And another thing...the brightness correction is a little too fast, very different from what happens with xbacklight or with gnomePmanager, isn't it one of those cases where the pixels are turned dark and not actually the light dimmed ? That would make it useless...

What is it in your experience? Remember that I use a thinkpad with its thinkpad ibm special module...maybe it's a little different I dont know.

---

### Post by Axx83 on 2008-09-27
> **Thingymebob said:**
> If i do xbacklight -set (anything) in a terminal I'm getting *"No outputs have backlight property"*
so I'm now poking around to find out how gnome power manager is doing it

weird, with both my laptops xbacklight doesn't give that response, actually with all acer's I've tried it on it doesn't do anything at all, just no feedback when i -set it to something. With thinkpads it works really well.

---

### Post by squaregoldfish on 2008-09-27
I don't know what happens if you have 2 LCD options - I've only got one on my Dell Inspiron. I would suggest setting both to be on the safe side. Perhaps one's for the external video port? Just a thought.

I too get an instant change in brightness, but it is changing the backlight brightness - with a watt meter plugged into the laptop, the power usage definitely decreases.

Steve.

---

### Post by Axx83 on 2008-09-27
> **squaregoldfish said:**
> I don't know what happens if you have 2 LCD options - I've only got one on my Dell Inspiron. I would suggest setting both to be on the safe side. Perhaps one's for the external video port? Just a thought.

I too get an instant change in brightness, but it is changing the backlight brightness - with a watt meter plugged into the laptop, the power usage definitely decreases.

Steve.

Well that's very good, I'll start using it right away, thanks for the tip ;-)

---

### Post by Axx83 on 2008-09-27
Ok I've added both the commands, one for video and one for wireless and they fuction smoothly, I consume now more or less 11 watts which gives me at least 2 hours 40 minutes of autonomy !!! Here's the final script:
```
#!/bin/bash
# on ac power
if on_ac_power; then
echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
echo 0 > /proc/sys/vm/laptop_mode
echo 10 > /proc/sys/vm/dirty_ratio
echo 5 > /proc/sys/vm/dirty_background_ratio
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
echo 100 > /proc/acpi/video/VID/LCD0/brightness
echo 100 > /proc/acpi/video/VID1/LCD0/brightness
echo 6 > /sys/bus/pci/drivers/iwl3945/*/power_level

else # on battery power
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 5 > /proc/sys/vm/laptop_mode
echo 40 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 50 > /proc/acpi/video/VID/LCD0/brightness
echo 50 > /proc/acpi/video/VID1/LCD0/brightness
echo 3 > /sys/bus/pci/drivers/iwl3945/*/power_level
fi
```
notes: the value '3' for iwl3945 is not the least consuming one, but it's a good compromise for those of us that have an older router. '5' would be the best, maybe when I buy a new device...
I've also disabled gnome-power-manager in managing backlight, with thinkpads it just doesn't work, with this sys interface it works perfectly. Put 40 or 30 in place of 50 if you can stand very dark screens, you will probably reach 10 watt this way.

Happy battery saving to all of you !

---

### Post by Thingymebob on 2008-09-28
Neither worked for me. I don't have the VID dirs in /proc/acpi/video just VGA/LCD dir the brightness file in there reads <Not Supported> so I came up with a rather ugly solution that works 
```

 i=0
while [ $i -le 5 ]
do 
/etc/acpi/video_brightnessdown.sh
i=`expr $i + 1`
  sleep .1
 done
```
which effectively presses my brightness down key 5 times, changed the command to /etc/acpi/video_brightnessup.sh in the AC power section

---

### Post by Axx83 on 2008-09-28
> **Thingymebob said:**
> Neither worked for me. I don't have the VID dirs in /proc/acpi/video just VGA/LCD dir the brightness file in there reads <Not Supported>

sysinterfaces are never the same on 2 different notebooks, I think I should mark my solution as viable only for laptops with this configuration:

Intel CPU
Intel motherboard chip
Intel graphics card
Intel wireless card

it's very easy to remember eheheheh

---

### Post by Thingymebob on 2008-09-29
Anyone reading who has ATI video should also do aticonfig --lsp ,find the number for the low voltage state then add aticonfig --set-powerstate=1 to the script (this knocked a further 5W useage on my system) - where 1 is the low voltage powerstate, don't forget to set it back in the AC.

for Atheros wireless use *iwconfig ath0 txpower 3* where ath0 is the interface

I'll post a version of Axx83 script here that works with ATI/Atheros/AMD when I've got everything working.

---

### Post by Axx83 on 2008-09-29
I'm sure something good is gonna come out of this teamwork :D

---

### Post by Thingymebob on 2008-10-01
Hope so, I have some time next week and may work on something that can figure out which tweak best suits the hardware the script is running on. I think I've got wireless sorted.

Does anyone no how to set Nvidia & Intel video cards power states - I know Nvidia has them (seen powermizer) don't know anything about Intel yet.

Not sure if I should also make it read in the current state of all these settings when its first run and store it somewhere then always restore to that?

---

### Post by Axx83 on 2008-10-01
> **Thingymebob said:**
> Hope so, I have some time next week and may work on something that can figure out which tweak best suits the hardware the script is running on. I think I've got wireless sorted.

Does anyone no how to set Nvidia & Intel video cards power states - I know Nvidia has them (seen powermizer) don't know anything about Intel yet.

Not sure if I should also make it read in the current state of all these settings when its first run and store it somewhere then always restore to that?

I think intel videocards are already preatty low voltage (and low power) by themselves, but maybe there is a command for that too.

Anyway while tuting the script I found out I had 3 more scsi hosts and added them to the script:
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
and so on

that helped me with wakeups, now I never go beyond 70...cutting probaly another 0.5 watts

---

### Post by Ub1476 on 2008-12-03
Hey man, I like your work. Haven't tried it yet though. :p

Anyway, does this work good with [tpfan]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script#tp-fan:_Automatic_daemon_with_GTK.2B_GUI")? Also, if you haven't, this script should be added to the ThinkWiki!

I'm using the Thinkpad X200. Is there any new information I can provide? 

Thank you :)

---

