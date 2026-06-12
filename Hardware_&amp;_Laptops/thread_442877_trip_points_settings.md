---
title: "trip_points settings"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by jgcamp99 on 2007-05-13
Anyone know of a way to replace the trip points with cooler temp settings by simply replacing this file ? It would be simpler to be able to open the file, set the temps lower than the default, save it and reboot. No scripts, less fuss. Otherwise I'll have to figure out a way to get the scripts to actually work.

BTW, this is with a Dell L400 notebook with Ubuntu 7.04.

---

### Post by jgcamp99 on 2007-05-15
Piddling with it, I was able to successfully change the trip_points, but only as "root". I created a /etc/acpi event, then I manually ran a .sh file that had the script:

echo 99:0:45:40:38 > /proc/acpi/thermal_zone/THRM/trip_points

By now, the temps had exceeded my new trip_points and the fan came on with no problem, stayed on until it reached the trip_point and then shut off. After this I logged out and tried it as the default Ubuntu user that was crated at install. Permissions denied to change the trip_points at this stage.

Next, I decided to go to the specific trip_points file as root. Couldn't get there so I had to change permissions to what I thought was just the proc folder to allow Group and others to modify the file (read-write permissions). Here's where I hosed Ubuntu. It locked my regular user out. I face a reinstall at this point. No biggie there, except this Dell L400 is a bear to install an OS on, as it's not a cdrom install but a PXE network/internet install.

Anyhow, resetting the trip points for me was relatively successful. It would be nice if Ubuntu would make this trip_points file accessible and editable to better values that enhance cooling. The other values would get the cpu too warm, so much that heat trapped in the notebook was heating up the hdd and that's where my lockups were occurring on occasion. I'd rather have the fan come on before 99:0:80:65 for this notebook @ about 40* C, that way heat is evacuated and the hdd runs in the mid to upper 30's instead of going to 47-50* C that it runs @ when the cpu has to get to 65* C before the fan comes on.

Well, back to a reinstall & theory here.

---

### Post by jgcamp99 on 2007-05-17
OK, reinstalled Feisty and I'm almost back to where I was software setup wise before mucking it up.

I can run as a root terminal in the default user I created during installation and then manually script changes to the trip_points. Wouldn't mind making this a permanent change. As I also have an Apple Powerbook 867, it had issues with staying cool too with Panther. Apple changed it and subsequently OS X Tiger to kick on about 47-48* C. So I figure Ubuntu/Linux being very similar, my trip points are manually over-ridden as:

echo 90:0:52:50:48 > /proc/acpi/thermal_zone/THRM/trip_points

cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           90 C
passive:                 52 C: tc1=2 tc2=3 tsp=40 devices=0xce4ca310 
active[0]:               50 C: devices=0xce4ca784 
active[1]:               48 C: devices=0xce4ca838 

(It was 99:90:80:65 prior to being manually over-ridden.)

Fan doesn't appear to be any more or less overactive than OS X (Tiger) and the Powerbook.

The difference, the heat is evacuated from the slim case and the temp under internet surfing while playing back HBR1 internet radio with Rhythmboxwirelessly is kept to 46-50* C. And just as I theorized, thought and hoped for, hdd temp is a constant 43* C. Battery life indicated seems to be about 5-10 minutes shorter because of the fan activity. Battery life never was great with this notebook, the battery is the original one from 1999-2000. It still lasts around 1:45-2:15 hours regardless of trip_point settings, so I don't think there is much sacrifice in terms of battery life if there is much at all. I'll probably monitor this over the next few days to get a more definitive feel for the behavior. Perhaps the bios battery calibration is in order because I reinstalled everything ?

Preliminarily (after roughly a couple of full-discharge battery cycles of observation), for now, my assessment of these preferences, the Dell L400 P III 700 trip_points are ideal @ this configuration for acpi fan activation trip_points. I hope this thread helps others that have this same level of discomfort for watching the cpu drive up to 65* C and their hdd creep up to 47-50* C.

---

### Post by jgcamp99 on 2007-05-17
After reboot, default installation trip_points in effect, temps are creeping upwards after just a few minutes. CPU = 54, HDD = 44. Nothing more to prove here, I'm going to reset trip_points to the lower settings with the root terminal command as watching the temps rise is just not acceptable anymore. That done, the fan kicked on within 20-30 seconds with the lower settings in effect. Within another couple of minutes temps are down to 45-48 for the cpu and 43 for the hdd and stabilized. Battery life isn't any worse than indicated before, even without a calibration after a clean install via PXE network installation.

Ubuntu/Canonical, please fix this permanently for me/us !

---

### Post by jgcamp99 on 2007-05-25
This procedure outlined below fixes it permanently to whatever you want to set the trip_points to. I happen to have set mine to these values:

"[B][I]#!/bin/bash
# Overwrite default trip points.

echo 90:0:52:52:50 > /proc/acpi/thermal_zone/THRM/trip_points[/I][/B]"

Step 1: I created a file called ***set_trip_points.sh*** as root with only this code in it, then made sure it was **executable**. 

Step 2: Directory placement of this file is critical. It goes here as this file:

***/etc/acpi/start.d/set_trip_points.sh***

Now when I boot up everytime, the system loads every *.sh in that folder as it always had, but now my set_trip_points.sh executable script is there and loads as well.

I rebooted, simply ran the:

"***cat /proc/acpi/thermal_zone/THRM/trip_points***"

in a terminal session and it verified the new trip_points settings indicated by my script. And sure enough, the true test is that the fan kicks on at 50* C, stays on long enough to cool it and it's been hovering around 47-48* C and best of all the hot air is vacuated from the case and my hdd is currently only 41* C. I couldn't be more pleased with it at the moment !

---

### Post by zero-9376 on 2007-06-28
ok so i have basically followed this setup for my via based laptop, the problem is that even with the trips at 45 deg. because the fan is on full blast it takes ages to get to that temp even with 100% cpu and so i have to deal with the noise.
When i set the temp to say 35-40, once the fan does slow down it is switching on and off far too often, every 30 seconds as this is what i set the polling freq. at, what i want to do is have a set the trip_points, sleep for 60 seconds to allow the temp to increase above 35 to slow the fan, then set the trip to 50.
What i dont want to do is cause the boot to slow by 60 seconds... this is what i plan on doing

#!/bin/bash
# Overwrite default trip points.
echo "90:0:57:57:30" > /proc/acpi/thermal_zone/THRM/trip_points #laptop starts cold at 25ish
echo "30" > /proc/acpi/thermal_zone/THRM/polling_frequency 
sleep 60s  #give it a minute to warm up
echo "90:0:57:57:50" > /proc/acpi/thermal_zone/THRM/trip_points #warm now but can deal with warmer for the sake of peace and quiet


is this a good idea, am i going to damage the system or with this make acpi slow and thus slowing boot even with feistys parrallel boot process. is there a better way?

---

### Post by zero-9376 on 2007-06-28
well for future reference this worked and did not appear to slow the boot process as far as i can tell. my computer is finally quiet

---

### Post by jgcamp99 on 2007-09-02
> **zero-9376 said:**
> well for future reference this worked and did not appear to slow the boot process as far as i can tell. my computer is finally quiet

The alternative for me was to use the default settings of Ubuntu. The battery on my Dell L400 lasts only a couple of hours and if I did light work with it, the heat just simmered the notebook. It didn't really have much effect on the cpu. Heck it's only a P III 733 anyway, how fast can this notebook be by today's standards ? But let's face it, as a internet and office application appliance it still can travel and do those things about as good as anything else you can buy that'll trounce it as a gamer or power user notebook. Under heavier workloads, the hdd felt the effects of 65* C. It shut itself down, wouldn't wake up, even though the hdd was told never to sleep anyway. About 40% of battery life remaining and I'd have to reboot it.

With the reset trip points, the system gets to the new trip points, the fan blows hard and gets the temp back down into the mid 40's for the cpu. Whatever heat is in the case, I want vacuated. The result is my hdd never gets overheated to the point of thermal lockup/shutdown to protect it, because if that ever fails, I'll be replacing hdd's constantly and reinstalling OS and applications.

For the most part, I rarely hear the fan, but when it hits that trip point, I want to hear it roar, the sooner that hot air is vacuated, the cooler every other part is inside it. The Dell L400 is an ultralight and slim notebook. closed it's barely the width of my thumb.

---

### Post by zero-9376 on 2007-11-08
just installed gutsy and while it appears to be better i would still like to be able to change the temps at which the fan kicks in but im getting

bash: echo: write error: invalid argument

anyone been able to do this on gutsy

---

### Post by Arch2 on 2007-12-02
This feature was removed in the 2.6.22 linux kernel.
[https://lwn.net/Articles/244595/](https://lwn.net/Articles/244595/)
to check your kernel version..
uname -r 
in Terminal

---

### Post by _Stevie_ on 2008-01-08
yep, too bad they removed it. one should think a linux user knows what hes doing.

---

### Post by Arch2 on 2008-05-07
Since they took away the ability to change the trippoint settings; and neither lmsensors nor i8kutils work on my system; I figured out another way to control the fan.

1)in System>Administration>Synaptic Package Manager search and install sensors-applet
2)rt ckick on taskbar(in an open area)> add to panel>click on 'Hardware Sensors Monitor'
The cpu temperature should now displays on task bar 
Next, in Terminal type...

sudo -s
(enter your password)
echo -e '#!/bin/sh \n chmod 646 /proc/acpi/fan/FAN0/state' > /etc/acpi/start.d/allow-fan-control.sh

This makes a script that runs on bootup that lets you turn the fan on/off.

Right click on the temperature display on the task bar> Preferences> Sensors tab> click on the arrow next to acpi> click on the THRM that shows up then click on Properties

place in low alarm command.....
echo -n 3 > /proc/acpi/fan/FAN0/state
This turns the fan off.

place in high alarm command.....
echo -n 0 > /proc/acpi/fan/FAN0/state
This turns the fan on.

Now set your Sensor Limits 
I set mine 55 for low and 60 for high 

Check enable alarm.
Sometimes my bios wants the fan off when I want it on,
so I set the alarm repeat interval to 5 sec.

Then to get rid of the pop up window; uncheck Display notifications under the Genreal Options tab.

---

### Post by _Stevie_ on 2008-05-08
Arch2, thats absolutely ingenious, thanks, will try that!

---

### Post by _Stevie_ on 2008-05-08
haha man, that worked absolutely great! :D
brilliant idea! thanks again ;)

---

