---
title: "laptop-mode confusion"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by edwardaux on 2006-11-23
I've migrated from XP to Ubuntu a few months ago and am very happy with the transition, with one small exception - battery life!  I've gone from getting around 2 hours on XP, to about 50 minutes using Dapper.
		
Anyway, looking around for a solution, I see that most people suggest configuring laptop mode.  However, I have to admit, I am having a mongrel of a time actually trying to figure out which package/executables I am supposed to install/run.
		
Looking at synaptic, I see that I have both "laptop-mode" and "laptop-mode-tools" installed (versions 0.4 and 1.11-1ubuntu3 respectively.)  What is the difference between these guys?
		
In my /usr/sbin directory, I have two executables: laptop_mode and laptop-mode - which of these am I supposed to run?  It seems that the options for the first are start|stop|auto, but for the second, they are start|stop.  My best guess indicates that I should be using laptop_mode, but I am not sure.  I *think* I want to run "laptop_mode auto", but the man page says that it is very dependant on /etc/init.d/laptop-mode.  There are other various reports saying that I need to edit /etc/default/laptop-mode, but then there are other reports saying I need to edit /etc/laptop-mode/laptop-mode.conf!
		
It is *very* confusing!!  All I want to do is have it switch into laptop mode when I unplug the AC power... my best guess is that I need to uninstall "laptop-mode" from synaptic, possibly configure /etc/laptop-mode.conf, run "laptop_mode auto" and hope that everything works from that point.  Is that correct?

Any advice would be much appreciated.  Thanks a lot.

--
edwardaux

---

### Post by dmartinsca on 2006-11-25
Hi there,

I use Edgy but from what i've read the setup should be the same on Dapper.

First off, uninstall laptop-mode. This is the outdated laptop-mode scripts from the linux kernel. laptop-mode-tools is a much more recent version.

Next up, edit /etc/default/acpi-support. Edit the ENABLE_LAPTOP_MODE line so it is true.

After changing this setting it may be enough to just unplug the power for laptop mode to start, or you may need to restart the acpi-support script.

```
sudo /etc/init.d/acpi-support stop
sudo /etc/init.d/acpi-support start
```

If that fails to make any changes take effect you can always just restart the pc. Oh, you can check if laptop mode is running or not by running **cat /proc/sys/vm/laptop_mode** A non-zero value indicates it is running.

That is basically all you need to do. If you'd like to change the default settings for laptop-mode, edit /etc/laptop-mode/laptop-mode.conf. In particular, i find these settings too low: ```
LM_AC_HD_IDLE_TIMEOUT_SECONDS=5
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=5
```
This is how long the hard drive needs to be inactive for before it shuts down. Set at 5 seconds i find the drive is spinning up/down far too often. I would rather not destroy my hard drive in 3 months. I set this for 25 seconds but it really depends on your habits.

After making changes to this file, running **sudo /etc/init.d/laptop-mode reload** should be enough to make the changes take effect.
You can find more information on the settings in this file by running **man laptop-mode.conf**

You don't need to run any of the laptop* commands on your own, once these two files in /etc/ are setup it should be an automatic process!

Hope this clears things up a bit!;)

---

### Post by Hillerd on 2006-11-27
What is your experience with laptop mode? 

I am also migrating from XP and battery live is reduced from 3.5h to 1.5h. There is actually not a big change (some minutes) with laptop mode, even though the HD is spinning down and the processor is running at minimum (600 MHz).So what is XP doing differently? Where can I tweak it more?

Another topic: is there the possibility to manually start and stop laptop-mode? Let's say via a script in the panel. E.g. when I am reading manuals, I like the HD to spin down, but when I am learning (by doing) Ubuntu, the HD should continue spinning.

---

### Post by reader4 on 2007-01-20
> **dmartinsca said:**
> If that fails to make any changes take effect you can always just restart the pc. Oh, you can check if laptop mode is running or not by running **cat /proc/sys/vm/laptop_mode** A non-zero value indicates it is running.

I am also running Edgy by having a hard time getting laptop mode to work just right.  I have done the same things you suggest, but this is what happens:

I am plugged in: **cat /proc/sys/vm/laptop_mode** = 0
I unplug the power supply: **cat /proc/sys/vm/laptop_mode** = 0
With the supply unplugged, I **sudo /etc/init.d/laptop_mode reload**, then **cat /proc/sys/vm/laptop_mode** = 2
I plug the supply back in: **cat /proc/sys/vm/laptop_mode** = 2
Again, I **sudo /etc/init.d/laptop_mode reload**, then **cat /proc/sys/vm/laptop_mode** = 0

So, it seems that my laptop mode is not seeing or resopnding to the event.  When I connect/disconnect, other things that should happen do: the screen dims, the box syaing I am on battery power comes on, etc. but laptop mode doesn't start.  Did you have this problem?  Any suggestions?

---

### Post by Hillerd on 2007-01-21
> So, it seems that my laptop mode is not seeing or resopnding to the event. 
On my laptop, I have to wait some time (I guess around 15s) before it recognizes the change.

This is what I did to set laptop mode[[http://www.samwel.tk/laptop_mode/index.html]](http://www.samwel.tk/laptop_mode/index.html])
. Actually the major impact was updating the ATI graphic card drivers.
```
sudo gedit /etc/default/acpi-support
ENABLE_LAPTOP_MODE=true
```
further settings:
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```
We are not controlling the hard disk
controlling the read ahead would only be useful if we wanted to spin the HD down
```
CONTROL_READAHEAD=0
```
if we wanted to have the HD spinned down, this should be enabled to avoid that journaling drives (ext3) would spin up HD occasionally
```
CONTROL_NOATIME=0
```
Spinning down the HD gives no real benefit and might cost life-time (also: the time setting might conflict with POWERMGMT)
```
CONTROL_HD_IDLE_TIMEOUT=0
```
Intrinsic HD power-management is already very good. Default setting seems to be 128 which gains 1.5W (9%) against off (255)
```
CONTROL_HD_POWERMGMT=0
```
The CPU frequency shall be reduced to minimum. This saves up to 5W or 25% compared to the performance setting (but only little compared to ondemand)
```
CONTROL_CPU_FREQUENCY=1
BATT_CPU_GOVERNOR=powersave
```

It's sufficient for me but still achieves only 2:30h instead of 3:30 as with WXP.

---

### Post by reader4 on 2007-01-21
Thanks!  I just wasn't being patient enough - looks like I have to wait a good 15s as well before it is recognized.  Really strange how much more battery life Linux seems to use... I would very interested to hear why, if anyone knows.  I have noticed more CPU fan noise than I used to with XP.  I know current devices like fans can draw a lot more energy from a battery, but I don't know the relative power consumption of fans/memory/HDD/CPU/etc.

---

### Post by Hillerd on 2007-01-21
> but I don't know the relative power consumption of fans/memory/HDD/CPU/etc.
While on battery, I have a battery symbol on my panel, it is the gnome-power-manager. Right-clicking and selecting "Information" you get a screen with various tabs. Playing with the laptop-mode options and counterchecking on this panel (always be patient, the system is reacting slowly; probably in order not to take away too much resources from important tasks), I came up with the power consumption and percentages.
If you are running an ATI graphics card, I recommend to install an update, that really made a huge difference for me. Let me know if you need help there.

Dietmar

---

### Post by reader4 on 2007-01-21
> **Hillerd said:**
> While on battery, I have a battery symbol on my panel, it is the gnome-power-manager. Right-clicking and selecting "Information" you get a screen with various tabs.

Hmmm, now I've done it.  I don't have that battery icon on my panel, I had it set to only come on when the battery state was critical.  I changed that, but the panel icon never showed up.  I tried restarting, but to no avail.  I will keep working with this, but do you know how to get to that information screen without right-clicking the icon?  Can you **ps aux** to find out what is running when you click it?

Thanks!

---

### Post by Hillerd on 2007-01-21
> Can you ps aux to find out what is running when you click it?
I am just starting with Ubuntu, so I am still an absolute beginner.
The program running is the gnome-power-manager. You can find it in Synaptics. Maybe reinstalling it could help? 
Help says: > GNOME Power Manager is usually started in GNOME startup, but
    you can manually start GNOME Power Manager by doing: 
gnome-power-manager --verbose --no-daemon
Furthermore I found >  The  programs  are documented fully on [http://gnome.org/projects/gnome-](http://gnome.org/projects/gnome-) power-manager/ .
Sorry, I am only a beginner and cannot really help here. Anyway, I have to be in the office tomorrow morning at 8, so it's time to bed. 
Good luck
Dietmar

---

### Post by reader4 on 2007-01-22
I am also a beginner with Ubuntu, but have been mostly pleased so far.  Just as an aside, I noticed my CPU fan going again when I had no apps running, which I thought was quite odd.  I ran **top** in a terminal and found that the evince-thumbnailer was using 90%+ of my CPU time!  I tried reinstalling and briefly looked around for ways to disable that feature, but could not find anything so I opted just to uninstall evince.  My system is much happier now.

---

### Post by ntetreau on 2007-01-22
You might want to take a look at this thread for a howto get laptop-mode to properly start at boot up (normally, laptop-mode only starts when your laptop is on and then you unplug it).  Also, we are working on scripts to enable automatically the power management on intel wifi cards.

link to the [thread]("http://www.ubuntuforums.org/showthread.php?t=339089")

---

### Post by reader4 on 2007-01-22
Does anyone have issues with slower system performance after coming out of laptop-mode?  A couple of times now I have noticed that after plugging AC back in, I still get the slower performance I had while on battery - menus opening, windows opening, etc.  I noticed CPU usage is something like 40-90% all of the time with most of the usage coming from firefox-bin and gnome-system-monitor.  When I shutdown and restart, CPU time is more like 7-10% with the system monitor using most of the time.  What causes this?  Is there a good way to look into this further?

---

### Post by Henry Rayker on 2007-01-24
reader4, your problem could be that, after coming out of safemode, your processor scaling isn't being set to the same mode it was before laptop-mode took over. Under laptop-mode, it is probably using a more conservative processor scaling mode than it would normally.

---

### Post by reader4 on 2007-01-24
This is what I thought as well, and it does seem to be the case.  So, I checked laptop-mode.conf and found that everything was in order... fastest CPU settings when on AC or NOLM, slower when in laptop mode.  I also looked inside **/sys/devices/system/cpu/cpu0/cpufreq**.
affected_cpus=0
cpuinfo_cur_freq=1500000
cpuinfo_max_freq=1500000
cpuinfo_min_freq=600000
scaling_available_frequencies=1500000 1200000 1000000 800000 600000 
scaling_available_governors=userspace powersave ondemand conservative performance
scaling_cur_freq=1500000
scaling_driver=centrino
scaling_governor=performance
scaling_max_freq=1500000
scaling_min_freq=600000

Interestingly, however, when I look in ./stats/time_in_state:
1500000 990013
1200000 3680
1000000 2408
800000 2640
600000 9947490

which (if I'm reading this right) shows that the CPU has spent the most time at 600000.  This is interesting because the only time I have used battery since installing Ubuntu is to checkout laptop mode, but I don't know about what other times Linux might scale frequencies even in normal mode.

So, is it possible that I am running at 600000 even though everything says I'm at 1500000?  Or could there be something else going on here?

---

