---
title: "powertop"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Okar on 2008-01-30
hi,
I recently bought a laptop.
To save some watts I installed [powertop]("http://www.lesswatts.org"). I run it with sudo so it has root rights.
It suggests different things to save watts, and I activated all that stuff, but as far as I restart my system these options are turned to default, or whatever, again.
How can I make this stuff permanent?

Furthermore what are the most important options if you want your system to last longer?

---

### Post by Wikzo on 2008-03-08
BUYP (Bring Up Your Post)

I have the same question: How do you make the Powertop changes permanent?

---

### Post by PurposeOfReason on 2008-03-08
Unless you are always on the road, it is a bad idea to keep a lot of that permanent. For me powertop tells hal to stop polling for devices (check for USB drives, CD's, etc.) and turns off bluetooth amongst other things.

---

### Post by Iceman512 on 2008-04-03
Apologies for resurecting a dead thread but I figured it would be better to bump this one instead of making another one exactly like it and cluttering up the forum. 

Anywho, how would one go about to make these changes permanent? I use my notebook (HP DV2550SE) at school almost exclusively so I need every minute I can get. 

Thanks in advance.

EDIT: I found this link: [http://ubuntuforums.org/showthread.php?t=618964](http://ubuntuforums.org/showthread.php?t=618964) and a user posted that anything in /etc/rc.local will be executed at boot. So, whatever suggestions Powertop makes, I should just copy and paste those lines into this script? Apologies for noobness but I don't want to break Ubuntu, it's too precious to me! Thanks in advance.

---

### Post by Whiffle on 2008-04-03
I would suggest to add anything you want done when running on battery to a script in

/etc/acpi/battery.d/

and then anything you want done upon returning to ac power to a script in

/etc/acpi/ac.d/

for example, 16-optimizations.sh  in my battery.d:
```

echo 5 > /proc/sys/vm/laptop_mode
echo 0 > /proc/sys/kernel/nmi_watchdog
echo Y > /sys/module/snd_ac97_codec/parameters/power_save
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 1 > $i; done

echo level 0 > /proc/acpi/ibm/brightness
hal-disable-polling --device /dev/scd0

ethtool -s eth0 wol d

hdparm -B1 -S12 /dev/sda

echo crt_disable > /proc/acpi/ibm/video
echo dvi_disable > /proc/acpi/ibm/video

ifconfig eth0 down


amixer set Line mute nocap
amixer set Mic mute nocap

iwpriv eth1 set_power 7


```

---

### Post by Iceman512 on 2008-04-03
hmm, is /etc/acpi/battery.d/ referring to the script file itself or just the folder? I ask because on Hardy, it refers to a folder with a script file called 15-anacron.sh. Do you recommend I just copy and paste your code into this file? Here is what 15-anacron.sh contains:

```

#! /bin/sh

# This script makes anacron jobs stop to run when the machine is
# unplugged from AC power, or suspended.

/usr/sbin/invoke-rc.d anacron stop >/dev/null   

```

Thanks in advance.

EDIT: Hmm, upon analyzing your code, it seems that simply copying and pasting won't do; will have to modify some names of devices and what not(though thatls childs' play for you linux experts out there;)

---

### Post by Whiffle on 2008-04-03
I would make a new file in battery.d.  All executable scripts in that directory get run whenever the machine switches to battery operation.  

Yeah you probably wouldn't want a direct copy paste of mine, some of it may not apply to yours.  I just put that there as an example, I have another script that unloads some modules and another that stops services.  Look through the /etc/default/acpi-support, i think some of that functionality might be built in.

---

### Post by Iceman512 on 2008-04-03
Hmm, powertop says to add this code:

```

SATA link power management
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

disable HAL polling
hal-disable-polling --device /dev/cdrom 

Increase VM dirty writeback time 
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs


```

Would I paste this stuff into the new file I'll be making? I assume the description of each line will have a # sign in front...Thanks again.

---

### Post by Whiffle on 2008-04-03
Yes and no, depends if those are the right devices (/dev/cdrom for example).  Run them by themselves in a terminal first to make sure they work.

---

### Post by jblackhall on 2008-04-03
Does anyone know why this command isn't working for me in terminal:
```
jonathan@jonathan-ubuntu:~$ sudo echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
bash: /sys/class/scsi_host/host0/link_power_management_policy: Permission denied

```

This is my output here:
```
jonathan@jonathan-ubuntu:~$ cat /sys/class/scsi_host/host0/link_power_management_policy
max_performance
```

---

### Post by Iceman512 on 2008-04-03
The code for SATA link power management gives error, permission denied, even when I tried running it with sudo. Same thing for Increase VM dirty writeback time. THe middle one worked so I'm going to add that one for now.

EDIT: Just realized that Jonathan is having a similar problem, lol.

---

### Post by jblackhall on 2008-04-03
Nevermind, apparently you have to enter a root shell.  Try this if you're having trouble:
```
jonathan@jonathan-ubuntu:~$ sudo -i
root@jonathan-ubuntu:~# echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
root@jonathan-ubuntu:~# exit
```

Now cat /sys/class/scsi_host/host0/link_power_management_policy should return min_power

If I put this in a script in battery.d, do I still need to spawn a root shell using sudo -i?

---

