---
title: "Thinkpad T60 Heating/Temperature issues"
date: 2008-06-07
forum: Hardware
---

### Post by eismcsquare on 2008-06-07
This is my first post here, so please go easy on me guys.

System:

Thinkpad T60
ATI Radeon X1400
Dual Core Intel T2400 1.83GHz
Intel Pro Wireless 3945ABG
Fingerprint Reader (not activated yet on Ubuntu)
Dual partition with XP and Gutsy

Problem: Laptop heating up/hight temperature. Laptop runs hotter on Ubuntu then when it runs on XP. Also, the area of right palm rest (near finger print reader) is hotter than that on left hand side.

Now, its not to the critical point that it shuts down automatically, but after frying my earlier laptop (Dell with Suse) due to probably bad power management, I am a lot more concerned here.

As my battery is dead, currently, system is plugged in all the time.

Here are my sensor temperature (in degree C) [from tpfan]
Sensor 0 57
Sensor 1 38
Sensor 2 38
Sensor 3 78
Sensor 8 43
Sensor 9 52
Sensor 10 51

Fan speed: 3436 rpm

This state is when I am not even running any Compiz effects. This is when all effects are disabled.

I have searched this forum/internet up and down, and have yet to see any solution - hence starting up this thread in hope that somebody knows more now than earlier and has a solution. Or at least somebody else is facing similar problem so that I know its not my setup but some hardware issue.

Here what I want to know first - If this is caused by fingerprint reader, would installed required driver/software for fingerprint reader and then enabling/disabling it would solve the problem? Has anybody done that?

Or that the problem is somewhere else entirely?

Other than this, I am simply loving Ubuntu.

Cheers!

---

### Post by eismcsquare on 2008-06-07
Forgot to highlight earlier.

See Sensor 3? **Its reading 78 C**. Its in the range of 70 when I start my T60 and hovers around 75 after a while. And that's bothering me a lot. What sensor is it? CPU, HDD?

---

### Post by cygnine on 2008-06-07
To get your cpu temperatures, type the following in a terminal:

```
cat /proc/acpi/thermal_zone/*/temperature
```

By the way, you're not the only one who's seen this heat problem in Ubuntu vs Windows. I also have a Thinkpad T60, with the same OS setup (except I'm running Hardy instead of Gutsy). Anyway, you might want to check out these threads:

[http://ubuntuforums.org/showthread.php?t=821597]("http://ubuntuforums.org/showthread.php?t=821597")
[http://ubuntuforums.org/showthread.php?t=813274]("http://ubuntuforums.org/showthread.php?t=813274")

I don't think this has anything to do with a fingerprint reader: I don't have one on my Thinkpad, and I have the same problems. And nobody else has been able to pin down their fingerprint reader as causing such a problem.

---

### Post by dinub1 on 2008-06-07
> **eismcsquare said:**
> This is my first post here, so please go easy on me guys.

System:

Thinkpad T60
ATI Radeon X1400
Dual Core Intel T2400 1.83GHz
Intel Pro Wireless 3945ABG
Fingerprint Reader (not activated yet on Ubuntu)
Dual partition with XP and Gutsy

Problem: Laptop heating up/hight temperature. Laptop runs hotter on Ubuntu then when it runs on XP. Also, the area of right palm rest (near finger print reader) is hotter than that on left hand side.

Now, its not to the critical point that it shuts down automatically, but after frying my earlier laptop (Dell with Suse) due to probably bad power management, I am a lot more concerned here.

As my battery is dead, currently, system is plugged in all the time.

Here are my sensor temperature (in degree C) [from tpfan]
Sensor 0 57
Sensor 1 38
Sensor 2 38
Sensor 3 78
Sensor 8 43
Sensor 9 52
Sensor 10 51

Fan speed: 3436 rpm

This state is when I am not even running any Compiz effects. This is when all effects are disabled.

I have searched this forum/internet up and down, and have yet to see any solution - hence starting up this thread in hope that somebody knows more now than earlier and has a solution. Or at least somebody else is facing similar problem so that I know its not my setup but some hardware issue.

Here what I want to know first - If this is caused by fingerprint reader, would installed required driver/software for fingerprint reader and then enabling/disabling it would solve the problem? Has anybody done that?

Or that the problem is somewhere else entirely?

Other than this, I am simply loving Ubuntu.

Cheers!

Ubuntu has (depending on circumstances and hardware in usage) a power management issue. It may occur randomly.
There is a CPU dynamic power allocation icon near or at the laptop battery icon. That dynamic power allocation usually runs the CPU at full clock speed (full power) when applications demand it, then goes back to lower cycles (lower power or lower cpu speed) when laptop is at idle or when applications are not demanding high power.
Ubuntu has a problem sometimes with that dynamic power allocation. 
It makes CPU run at full speed, even when applications do not require that. That causes CPU overheating.

I have seen this type of overheating before and this includes my own laptop (a HP model which is overall excellent). In my case it happened when I upgraded from version 6 to version 7. I did not have problems with my laptop with prior version of Ubuntu as I did not have any issues running MS Windows XP on it. Also not with other Linux distros run from Live CDs and not with Ubuntu itself, same version, also run as a live CD.

I also noticed that same overheating problems did not occur with same version of Ubuntu running on a desktop. So after backing up important data under Ubuntu, I wiped clean the Ubuntu partition and reinstall Ubuntu 7 clean from scratch from a CD.
Instl went without a glitch and since then i do not have overheating problems with Ubuntu. Currently running version 8.04 and it runs good.

So you may just try that. Then copy back files that you backed up  onto the Ubuntu partition.

If you do not want to do this, you can try playing with the dynamic allocation power icon. It can be set to 3 positions: power save, dynamic and performance. When set to dynamic it automatically allocated CPU power when needed. But that may have the glitch. You can manually set that icon to powersave mode, lower CPU cycles, that will reduce the clock cycles and therefore the overall temperature, but also reduce the CPU speed. Laptop will work slower, but with less heat. When you need faster speed, crank the icon to performance mode. That will crank the CPU speed to max. and therefore temps will rise. You can play with that on demand. If you are afraid of frying your machine, then put it on power save mode.
See what you get. Good Luck.

---

### Post by eismcsquare on 2008-06-11
Thanks cygnine, dinub1.

At least now I know that CPU temperatures are not that bad.

```

$ cat /proc/acpi/thermal_zone/*/temperature
temperature:             51 C
temperature:             50 C
```

I did check other threads, but they don't answer what is going on. This issue seems to be more common in T60, although not exclusive to them.


dinub1, I could not find that icon anywhere on my desktop. I can go to power history from the "plugged" icon. But then, I don't have a battery at the moment on my laptop anyways.

I will keep looking and post more info if I find any.

Thanks.

---

### Post by eismcsquare on 2008-06-11
Further update - still working on it:

Tried using fan control by following this how-to:
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

It seems I can set level to 7, and the fan speed increases to ~3780 rpm. But that is not making any big difference in the temperature.

Also, interesting to note that I can not put fan in "disengaged" mode - within few seconds of setting it, it resets to "auto".

---

### Post by dinub1 on 2008-06-12
> **eismcsquare said:**
> Thanks cygnine, dinub1.

At least now I know that CPU temperatures are not that bad.

```

$ cat /proc/acpi/thermal_zone/*/temperature
temperature:             51 C
temperature:             50 C
```

I did check other threads, but they don't answer what is going on. This issue seems to be more common in T60, although not exclusive to them.


dinub1, I could not find that icon anywhere on my desktop. I can go to power history from the "plugged" icon. But then, I don't have a battery at the moment on my laptop anyways.

I will keep looking and post more info if I find any.

Thanks.

You are welcome. The icon looks like a  yellow diamond and you can find it in the Ubuntu lower panel tray, at your right.... not on the desktop, but on the panel (taskbar).  I talk about Kubuntu. It shows if you have battery or not, also on desktops. When you move your mouse over it, it should say something like "CPU mode dynamic". By right clicking on it you can manually change its mode... as I stated, default is  the dynamic mode, the other options are power save and performance. In dynamic mode OS should adjust clock speed automatically depending on the programs. If it gets screwed up it may get stuck on Performance mode, then your CPU runs at full cycles and it overheats. In my experience this is only a Ubuntu issue. It does not happen with by example Mint that is a derivative of Ubuntu or other Linux distros. And this happens randomly.

---

### Post by dvchops on 2008-06-23
I am having the same problem. I have a t60 with the 2.16 core 2 duo cpu, and it seems to be running a bit hotter than with gutsy. It is idling around 60-65c, in a room with ambient temperature of ~80 Farenheit. I don't remember it idling that high in gutsy.

The third sensor is your GPU temperature, and like yours mine is around 80c at idle. That number seems high, it worries me. I never monitored it in gutsy, so I don't know if it has changed. 

Under the right side of your palm rest is the hard drive, that is probably the cause of the warmth there.

I'll play with power management more when I get a chance. What do people use to monitor temps in windows? I hardly use it anymore, so I have a tough time finding the good apps from the bloatware and spyware.

Dan

---

### Post by dvchops on 2008-06-23
You can also try to lower your cpu temperature with a different dynamic frequency scaling setting. Try this link: [http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

I changed my governor to 'conservative' and it tends to stay at the 1ghz more often, I think I lowered the cpu temperature 2-4 degrees celsius from that change. It's down to 58c now.


```
root@mediator:/sys/devices/system/cpu/cpu0/cpufreq# cat scaling_governor 
ondemand
root@mediator:/sys/devices/system/cpu/cpu0/cpufreq# echo conservative > ./scaling_governor 
root@mediator:/sys/devices/system/cpu/cpu0/cpufreq# cat scaling_governor 
conservative
```

[http://www.phoronix.com/forums/showthread.php?t=6522](http://www.phoronix.com/forums/showthread.php?t=6522)
Based on this thread I see there is an app called 'radeontool' that may be able to improve the GPU's power consumption in similar radeon GPUs, although our x1400 gpu is some sort of deformed model that crashes when the code is run. 

From the same thread I saw that there is an option in aticonfig called '--set-powerstate' that looks like it would be a big help, if it worked for me. Based on the error message my second monitor seems to be the problem, and I'm not about to give that up.

```
root@mediator:~# aticonfig --set-powerstate=2
Setting the requested power state failed or is not supported yet.
Possible reasons for failure:
  - thermal control is in effect
  - trying to set the current power state again
Modes unsupported due to bandwidth limitations:
  - dual head/big desktop/clone modes
aticonfig: parsing the command-line failed.
```

I'll keep playing around some other evening, but if I can't get reasonable temps I might just switch back to gutsy. :(

Dan

---

### Post by djmurf on 2009-12-11
Just wanted to add to this. 

I recently upgraded to Ubuntu 9.10, and noticed my T61 laptop had been running real hot. I was running through a long java build, and temps climbed up to 89C, and I've been able to "feel" the heat when using the laptop ( from my hands on the keyboard )

This is a T61 with core 2 duo 2.0ghz Nvidia graphics. 

I was sure it had something to do with the upgrade, but of course since I just upgraded, I was being ultra-sensitive to problems as most of us probably are. 

I tried everything, cpu script that would kick up the fan, and this did seem to help, although it didn't make any sense that I had to do this all of a sudden. 

After a few days of this, I finally decided top open it up, and see what was going on. 

I followed the field manual for pulling the keyboard, mouse bezel, frame bezel, speaker, and finally the fan, which is part of the heat sync assembly for the cpu and nvidia gpu. 

What was very interesting was 3 of the 4 cpu/fan screws were pretty tight, and one was almost finger loose ( probably the main cause here ). 

I went ahead and cleaned all of the grease off, and put on some new silver paste for both the cpu & gpu. 

Put her all back together, and voilla... back to normal temps. 

cpu at idle is about 44/45, gpu at 51.

Under full load it hits about 69 max on the cpu. 

I guess the moral of my story is pay attention to the hardware, don't always look at the OS. Under normal conditions, the hardware is taking care of the fans & temps. If you're all of a sudden seeing high temps and nothing is running hard, or you're seeing temps above what you're used to seeing under load, look at your fans, syncs, & thermal paste. There's a good chance that's where your problem is.

---

### Post by musarraf172 on 2009-12-12
> **eismcsquare said:**
> This is my first post here, so please go easy on me guys.

System:

Thinkpad T60
ATI Radeon X1400
Dual Core Intel T2400 1.83GHz
Intel Pro Wireless 3945ABG
Fingerprint Reader (not activated yet on Ubuntu)
Dual partition with XP and Gutsy

Problem: Laptop heating up/hight temperature. Laptop runs hotter on Ubuntu then when it runs on XP. Also, the area of right palm rest (near finger print reader) is hotter than that on left hand side.

Now, its not to the critical point that it shuts down automatically, but after frying my earlier laptop (Dell with Suse) due to probably bad power management, I am a lot more concerned here.

As my battery is dead, currently, system is plugged in all the time.

Here are my sensor temperature (in degree C) [from tpfan]
Sensor 0 57
Sensor 1 38
Sensor 2 38
Sensor 3 78
Sensor 8 43
Sensor 9 52
Sensor 10 51

Fan speed: 3436 rpm

This state is when I am not even running any Compiz effects. This is when all effects are disabled.

I have searched this forum/internet up and down, and have yet to see any solution - hence starting up this thread in hope that somebody knows more now than earlier and has a solution. Or at least somebody else is facing similar problem so that I know its not my setup but some hardware issue.

Here what I want to know first - If this is caused by fingerprint reader, would installed required driver/software for fingerprint reader and then enabling/disabling it would solve the problem? Has anybody done that?

Or that the problem is somewhere else entirely?

Other than this, I am simply loving Ubuntu.

Cheers!

I don't know whether it will help you or not. I had the same issue with my R51 (Lenovo IBM ).  And I got some abnormal sound in the m/c. I opened the m/c and found that the fan blades are broken. I have replaced the CPU fan and now it is running perfectly..

---

### Post by macaws on 2009-12-23
Hello,

I came to the forum looking for help on this same issue. Any insight would be appreciated. I have a Thinkpad T61, and since installing Ubuntu Karmic desktop edition, a week ago, my hard drive has been extremely hot. Some notes:

- This is *not* a dirty fan issue, as I have recently reinstalled a worn out fan and heatsink. 
- This has nothing to do with the CPU, because the hot area is directly over the hard drive.
- I notice that the hard drive spins all day long, whereas it was quiet on XP. Even during periods of inactivity, the drive is never "spun down." 
- This issue is a problem for a hot hard drive, hot hands, and general system wear from heat. The fan spins at maximum RPM all day, which will wear out the fan, also.

I used iotop to see which programs are writing to disk, and it appears that [kdjoural2] writes to disk about once per minute. There is another command with "log" in the name that writes occasionally but it flashed onscreen quickly and I did not catch the name. I think there are two problems:

1) The setting to "spin down the drive when inactive" seems to be "disabled" when on AC power. I believe this is via laptop-mode settings, but am not sure. I have switched laptop_mode in the config file to enabled, but this made no difference. I am not sure what steps to take to make sure laptop mode indeed turns on, and the drive indeed spins down when inactive. Maybe the laptop-mode settings are not the right idea. Is there a setting I should be using with hdparm to make the hard drive spin down?

2) Even if laptop_mode is enabled, the frequent logfile writes might prevent the drive from ever spinning down (or worse, make it spin up and spin down once per minute, all day long). Does anyone have any ideas to solve this? I am a new Linux user and do not know which logs are essential, which can be turned off, how to turn them off, etc. I installed BUM to check my services, and I see that rsyslogd is already off. The pesky log file every minute is called kdjournal2 and sometimes pflush. I do not know what these do or how to disable them. An internet search did not help me.

Thanks very much in advance!
-V

---

### Post by FrancoNero on 2010-07-22
bump...

my thinkpad gets ridiculously hot. just having it on is apparently enough... fan currently running, can't even manage to keep up. but there's nothing that woul dindicate cpu activity, it's just hot...

---

### Post by dvchops on 2010-07-22
A few months ago I was using some compressed air, decided to give my CPU vent a good squirt and a bunch of dust came out. Temps are 5-10c cooler all the time now. I should've done it a long time ago, but forgot about the possibility of dust building up in there since it's a laptop.

So, make sure your laptop is clean and dust free!

Now, with an ambient temperature of about 85 degrees f and minimal system load with two monitors on ubuntu 9.10, my cpu temp is 52 degrees C and GPU is 70 degrees C. GPU is still a little high, but much better than it was. With lower ambient temperature they also get much lower.

---

### Post by dante.jones on 2010-07-28
Hi eismcsquare,

There are two further options you should consider that will impact on the generation of heat on your laptop:

[LIST]
[*]Lack of dynamic power management with KMS enabled on the radeon video driver
[*]Excessive Wakeups generated from <kernel scheduler>
[/LIST]

[SIZE="3"]KMS Lacking dynamic power management[/SIZE]

The lack of dynamic power management with KernelModeSetting (KMS) when using the radeon driver is due in part to the kernel version of 10.04, and there may not be any immediate solutions to the problem without changing the kernel version to 2.6.34 or higher.

While in Ubuntu 8.04 dynamic power management on the radeon driver was handled effectively by using:

```
   Option          "DynamicClocks"  "on"
```

in your
> 
/etc/X11/xorg.conf

Sadly, this option will now not work with the current version of the radeon driver in Ubuntu 10.04. Given that 10.04 is a LTS version, lets hope this issue gets addressed elegantly, and soon.

A possible solution is to use the ATI non-open drivers.

Here's some reference for [KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting") (KMS)


[SIZE="3"]Excessive Wakeups from <kernel scheduler> [/SIZE]

There's a bug in the current version of the kernel Ubuntu 10.04 uses, that leads to many more wakeups generated by the kernel scheduler than in previous versions. This leads to a lot more work, and thus heat generated on laptops. It's [mentioned here]("http://ubuntuforums.org/showthread.php?t=1390055") and bug has been [logged here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552020").

---

### Post by Eibwen Xunil on 2010-08-27
> **djmurf said:**
> Just wanted to add to this. 

I recently upgraded to Ubuntu 9.10, and noticed my T61 laptop had been running real hot. I was running through a long java build, and temps climbed up to 89C, and I've been able to &quot;feel&quot; the heat when using the laptop ( from my hands on the keyboard )

This is a T61 with core 2 duo 2.0ghz Nvidia graphics. 

I was sure it had something to do with the upgrade, but of course since I just upgraded, I was being ultra-sensitive to problems as most of us probably are. 

I tried everything, cpu script that would kick up the fan, and this did seem to help, although it didn't make any sense that I had to do this all of a sudden. 

After a few days of this, I finally decided top open it up, and see what was going on. 

I followed the field manual for pulling the keyboard, mouse bezel, frame bezel, speaker, and finally the fan, which is part of the heat sync assembly for the cpu and nvidia gpu. 

What was very interesting was 3 of the 4 cpu/fan screws were pretty tight, and one was almost finger loose ( probably the main cause here ). 

I went ahead and cleaned all of the grease off, and put on some new silver paste for both the cpu & gpu. 

Put her all back together, and voilla... back to normal temps. 

cpu at idle is about 44/45, gpu at 51.

Under full load it hits about 69 max on the cpu. 

I guess the moral of my story is pay attention to the hardware, don't always look at the OS. Under normal conditions, the hardware is taking care of the fans & temps. If you're all of a sudden seeing high temps and nothing is running hard, or you're seeing temps above what you're used to seeing under load, look at your fans, syncs, & thermal paste. There's a good chance that's where your problem is.

  I had the same problem with my Thinkpad T61.  For several years I thought it was a software problem.  The BIOS has a high temperature threshold before the fan starts up.  I used TPfan but it still couldn't keep temperatures in check.    After 2 years of abnormally high temperatures (idle 60 C with gpu at 63 C, and high load at 85 C with gpu at 89 C) my fan finally gave out and I had to replace it.  Upon removing the heatseat I noticed that the manufacturer had slopped on copious amounts of thermal paste.  After replacing the heatsink, my laptop runs at a cool 45 C idle.  It's a huge difference and I suggest everyone who has a laptop with heating issues to remove and reapply the thermal paste.

---

