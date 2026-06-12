---
title: "Ubuntu 7.10 power management"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by dale-b on 2008-02-24
In my quest to figure out why my Thinkpad T43 gets only half the battery time in Ubuntu 7.10 than it does in XP, I edited two files,
 
/etc/default/acpi-support
/etc/laptop-mode/laptop-mode.conf

and changed a few values.  Upon rebooting I was delighted to notice right away that the hard drive was now spinning down until it was needed.  I thought I was on the trail to better power management.  That lasted for only a few minutes, then it went back to its previous behavior, that is, running all the time. It has remained so ever since.

Anyone know why it would do this?

---

### Post by kevmitch on 2008-02-24
What did you change in those files? What programs/daemons are you running when you find it spinning up a lot. Most likely, something is using the disk at regular intervals and causing it to spin up. Try running the command "lm-profiler" to get an idea of what applications are causing the spinups. 

As for power saving in general. I'm not sure if disk spinups alone will account for a 50% decrease in battery life. What cpu frequency governor are you using? Find out by running
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

The answer should be "ondemand", at least for relatively recent Intel chips (not sure about others). If its not, then my recommendation would be to install cpufrequtils which will make sure all the right modules are loaded and the correct governor is set on boot. Since it is not a daemon proper, it won't take up any resources after its init scripts have run. It just makes sure everything is set correctly and then exits.

You might also want to check out the powertop package which will tell you which programs are waking up your cpu and causing it to use more power. 

Finally, I would recommend checking to see if your graphics or wireless chips have powersaving features that are possibly not being utilised.

---

### Post by jespdj on 2008-02-25
If you want to increase battery life on your laptop, have a look at [PowerTOP](http://www.lesswatts.org/projects/powertop/).
```
sudo apt-get install powertop
```

---

### Post by dale-b on 2008-02-25
I edited /etc/default/acpi-support to say:

ENABLE_LAPTOP_MODE=true


I edited /etc/laptop-mode/laptop-mode.conf to say:

CONTROL_HD_POWERMGMT=1
CONTROL_CPU_FREQUENCY=1


I installed the cpu frequency monitor, which seems to be working.  It's set to "ondemand" and says 800 MHz most of the time, jumping to 1.73 GHz under load or if I plug in the AC power.

I installed Powertop a few days ago.  
ipw2200 is my wireless.  I have no idea what those things on the first line mean.


Below is a current Powertop output:

-------------------------------------------------------
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 1.0%)         1.74 Ghz     0.0%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2                9.3ms (99.0%)         1066 Mhz     0.0%
C3                0.0ms ( 0.0%)          800 Mhz   100.0%
C4                0.0ms ( 0.0%)

Wakeups-from-idle per second : 106.7    interval: 15.0s
Power usage (ACPI estimate): 16.4W (1.9 hours)

Top causes for wakeups:
  34.5% ( 38.8)       <interrupt> : uhci_hcd:usb1, yenta, eth0, i915@pci:0000:00
  16.1% ( 18.1)       <interrupt> : extra timer interrupt 
  13.2% ( 14.9)       <interrupt> : ipw2200 
   9.1% ( 10.3)       <interrupt> : libata 
   5.0% (  5.6)       <interrupt> : acpi
   3.3% (  3.7)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)

---

### Post by kevmitch on 2008-02-28
There's definitely something up with those first few powertop lines. It looks like you aren't getting below the C2 sleep state. The actual process-by-process wake ups don't look too bad though. Still my guess is that something is not letting your CPU go to sleep when it should. I think there may have been an issue with Intel graphics drivers for xorg when DRI was enabled that caused a similar symptom. You wouldn't happen to haven intel graphics chipset would you. If so, try either disabling DRI by adding 
```
 Option "NoDRI" 
```
under the "Device" section of your /etc/X11/xorg.conf, or better yet, update to the latest Intel drivers which have fixed this problem.

Other than that, I might try killing off processes one by one until you start to see your CPU spending most of its time in the C3 and/or C4 states when idle. Also what module in addition to ondemand are you using for cpu scaling? I think acpi_cpufreq is preferred if it works with your hardware.

---

### Post by raiwo on 2008-02-29
how the hell you get wakeups so low? Aren't they backporting that new improved intel driver to gutsy?
```
Wakeups-from-idle per second : 546.5    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  27.8% (111.9)       <interrupt> : uhci_hcd:usb5, yenta, i915@pci:0000:00:02.0
  13.8% ( 55.4)   operapluginwrap : schedule_timeout (process_timeout) 
  11.7% ( 46.9)       <interrupt> : HDA Intel 
  11.6% ( 46.6)       <interrupt> : uhci_hcd:usb2 
   8.8% ( 35.3)              Xorg : do_setitimer (it_real_fn) 
   5.1% ( 20.4)       <interrupt> : ohci1394, wifi0 

```

---

### Post by kevmitch on 2008-02-29
I found that the new 2.6.24 kernel does an amazing job of reducing wakeups. This is especially the case for 64 bit users as it is the first release to offer them a tickless kernel. Is that what you're running dale-b? That is an impressively low number of wakeups.

---

### Post by dale-b on 2008-03-01
I tried Kevmitch's suggestion about DRI, and look at this output from Powertop now:  
---------------------------------------------------------------------------
     PowerTOP version 1.8       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 0.8%)         1.74 Ghz     0.0%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2               11.8ms (99.2%)         1066 Mhz     0.0%
C3                0.0ms ( 0.0%)          800 Mhz   100.0%
C4                0.0ms ( 0.0%)

Wakeups-from-idle per second : 84.3     interval: 15.0s
Power usage (ACPI estimate): 15.6W (3.0 hours) (long term: 16.4W,/2.8h)

Top causes for wakeups:
  20.6% ( 12.1)       <interrupt> : extra timer interrupt 
  18.7% ( 10.9)       <interrupt> : ipw2200 
  13.4% (  7.9)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)
   8.2% (  4.8)       <interrupt> : uhci_hcd:usb2
   6.9% (  4.1)              Xorg : do_setitimer (it_real_fn)
   3.6% (  2.1)   multiload-apple : schedule_timeout (process_timeout)
-------------------------------------------------------------------------
It looks completely different.  The Intel 915 graphic thing is gone.  Wakeups are down.  Something's going right!

Now if I could just get the CPU speed down a bit.

Thanks Kevmitch.

---

### Post by raiwo on 2008-03-01
is there any other solution than Option "NoDRI" because i really want to use all the fancy compiz effects?

---

### Post by kevmitch on 2008-03-01
Ah yes, I guess it was apparent that you had an Intel chip from your powertop output. Indeed it does appear that disabling DRI reduces wakeups. I guess this isn't too much of a surprise because it appears this causes the graphics chip to no longer need that interrupt at all. It does not however appear that this is what was causing your cpu to stay mostly in the C2 state as that hasn't changed. You likely have the fixed version of the driver anyway. This was a bit of a shot in the dark. If you want to be sure, you can run 
```
apt-cache policy xserver-xorg-video-intel
```
To see what is installed. I've got 2.2.1 and it isn't preventing me from going below C2 with DRI enabled. Even with the DRI bug fixed though, it looks like NoDRI might still help out a bit. If you prefer to save a bit of power at the expense of graphics performance, then keep this option.

Here are a couple other things to check:
Make sure that you get answer of at least 4 by running
```
cat /sys/module/processor/parameters/max_cstate
```

Also make sure that "hpet" is the answer to.
```
cat /sys/devices/system/clocksource/clocksource0/current_clocksource
```

Is powertop giving you any suggestions at the bottom?

Oh and raiwo, if you don't use any cardbus cards, you might try 
```

rmmod yenta
echo blacklist yenta >> /etc/modprobe.d/blacklist

```

Also, it looks like your doing quite a bit of stuff while powertop is gathering statistics. Try closing your browser, stopping any sound and not touching your mouse. This should give you a good baseline.

---

### Post by dale-b on 2008-03-02
> **kevmitch said:**
> Ah yes, I guess it was apparent that you had an Intel chip from your powertop output. Indeed it does appear that disabling DRI reduces wakeups. I guess this isn't too much of a surprise because it appears this causes the graphics chip to no longer need that interrupt at all. It does not however appear that this is what was causing your cpu to stay mostly in the C2 state as that hasn't changed. You likely have the fixed version of the driver anyway. This was a bit of a shot in the dark. If you want to be sure, you can run 
```
apt-cache policy xserver-xorg-video-intel
```
To see what is installed. I've got 2.2.1 and it isn't preventing me from going below C2 with DRI enabled. Even with the DRI bug fixed though, it looks like NoDRI might still help out a bit. If you prefer to save a bit of power at the expense of graphics performance, then keep this option.

Here are a couple other things to check:
Make sure that you get answer of at least 4 by running
```
cat /sys/module/processor/parameters/max_cstate
```

Also make sure that "hpet" is the answer to.
```
cat /sys/devices/system/clocksource/clocksource0/current_clocksource
```

Is powertop giving you any suggestions at the bottom?

Oh and raiwo, if you don't use any cardbus cards, you might try 
```

rmmod yenta
echo blacklist yenta >> /etc/modprobe.d/blacklist

```

Also, it looks like your doing quite a bit of stuff while powertop is gathering statistics. Try closing your browser, stopping any sound and not touching your mouse. This should give you a good baseline.



apt-cache policy xserver-xorg-video-intel gives me:
  Installed: 2:2.1.1-0ubuntu9
  Candidate: 2:2.1.1-0ubuntu9


cat /sys/module/processor/parameters/max_cstate yields:
8


cat /sys/devices/system/clocksource/clocksource0/current_clocksource says:
acpi_pm

---

### Post by dale-b on 2008-03-02
And yes, powertop is suggesting that I put my wireless, AC97, USB, and some other things into a power-saving state.  I don't know how to do any of this.

---

### Post by kevmitch on 2008-03-03
Ok, first try this:
```
echo -n hpet > /sys/devices/system/clocksource/clocksource0/current_clocksource
```
You should then get "hpet" from cating that file. If that works, then you can set this permanently by adding a kernel boot parameter as follows:
Open up /boot/grub/menu.lst in a text editor and find the line that looks something like this amid the comments at the beginning:
```

# kopt=root=/dev/sda5 ro

```
The funny thing is that this isn't really a comment, it is an instruction for the update-grub script for what to add as options to the automatically generated kernel entries below when it is run. You will of course probably have something different for your root filesystem device, or you may have additional options like "resume=/dev/sda3" or "vga=792", but adding "clocksource=hpet" to the end of the line should force the kernel to use the hpet timer which is better for letting the processor sleep. So it should now look like
```

# kopt=root=/dev/sda5 ro clocksource=hpet

```
Save that and run the command 
```

update-grub

```
After reboot, you should then hopefully find that the clocksource file in sysfs will be set to hpet automatically.

Also what kernel version are you using?
```

uname -a

```
Like I said, 2.6.24 has quite a few power saving improvements one of which is AC97 powersaving for intel sound chips so you might want to upgrade to that if you aren't running it already. In general, take a look at lesswatts.org for how to implement the various suggestions that powertop gives you.

---

### Post by dale-b on 2008-03-04
Thank you so much for your suggestions and your help. Some of these ideas don't work for me, such as:
echo -n hpet > /sys/devices/system/clocksource/clocksource0/current_clocksource

This gives me "permission denied" so I can't proceed.

I will be home in a few days where I will have access to high speed Internet and can pursue this further.

BTW, my kernel is 2.22.

Thanks again for your help.

---

### Post by raphenry on 2008-03-04
i have a sony viao with the amd chip, i installed the powertop but dont know how to access it, and the  echo -n hpet > /sys/devices/system/clocksource/clocksourc0/current_clocksource
says that it does not exist.

help

---

### Post by Whiffle on 2008-03-05
Well, I'm not running gutsy, but I thought I'd post up so we can compare (I have T43 as well, intel graphics).  

Here is where I am at with regards to power consumption:
```

     PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 0.1%)         1.87 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.60 Ghz     0.0%
C2                0.0ms ( 0.0%)         1333 Mhz     0.0%
C3                0.0ms ( 0.0%)          800 Mhz   100.0%
C4              198.5ms (99.9%)

Wakeups-from-idle per second :  5.0     interval: 3.0s
Power usage (ACPI estimate): 13.5W (3.0 hours) (long term: 14.1W,/2.9h)

Top causes for wakeups:
  45.5% (  1.7)              Xorg : do_setitimer (it_real_fn)
  36.4% (  1.3)              Xorg : schedule_timeout (process_timeout)
   9.1% (  0.3)     <kernel core> : queue_delayed_work_on (delayed_work_timer_fn)
   9.1% (  0.3)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_time
r)

```

It estimates 3 hours of battery life, and that was at 80% battery life.  I had wireless off, the hard drive spun down, and the screen brightness as low as it goes.  I've got kind of a dirty hacks list of optimizations that run whenever I unplug the power cord.  If I ever get time, I'll make it into a script or something else a little smarter.
```

echo 5 > /proc/sys/vm/laptop_mode  #start laptop mode (this might be redundant)
echo 0 > /proc/sys/kernel/nmi_watchdog #stop the watchdog 
echo Y > /sys/module/snd_ac97_codec/parameters/powe2.6.24.22.6.24.2r_save #set power save on AC97 (this might be redundant)
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor # set cpu scaling gov (this is probably redundant)
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 1 > $i; done  #tell usb devices to autosuspend

/etc/init.d/preload stop  # i think thsi was creating alot of wakeups, so i made it stop
/etc/init.d/sysklogd stop  #this was writing to the hard drive every so often
/etc/init.d/ssh stop #I generally don't plan to ssh into my computer when its running battery
/etc/init.d/apache stop #I don't even know why I have apache...
/etc/init.d/bluetooth stop #i do use bluetooth, but not very often.


hdparm -B1 -S12 /dev/sda  #spindown timeout for hard drive

echo crt_disable > /proc/acpi/ibm/video #shut off VGA output
echo dvi_disable > /proc/acpi/ibm/video #shut off another output

ifconfig eth0 down #shutdown wired etherent (I can't remember the last time I used it)

modprobe -r pcmcia # unload pcmcia modules, responsible for wakeups
modprobe -r yenta_socket #ditto
modprobe -r uhci_hcd #usb 1.1 drivers, responsible for many many wakeups
#modprobe -r thinkpad_acpi #i usually unload this manually, causes alot of wakeups.  Also screws with suspending if i have it unloaded
modprobe -r tg3 #driver for wired ethernet, almost never need it
modprobe -r rfcomm #part of driver for bluetooth
modprobe -r bluetooth #bluetooth driver
modprobe -r irda # i dont use irda


amixer set Line mute nocap  #mute line -in, if its not muted AC97 won't powersave
amixer set Mic mute nocap #mute mic, ditto

iwpriv eth1 set_power 5 #set powersave mode on wireless.  If I'm not using wireless, I unload the ipw2200 module entirely

killall hald-addon-storage #stops polling of the cdrom, among other things
killall conky  #conky tends to make alot of wakeups as well.

```

Those are the things that seem to help the most.  I've got a 2.6.24.2 kernel that I've did a bit of customizing to, I can post the config for it if anyone wants it.  

I think its possible to get lower power usage than what I have, but I havn't had time to mess with it.  I find that some applications and drivers are really power hungry, such as wireless, thinkpad_acpi, conky, gnome-power-manager, and usb 1.1 drivers.  Most of that you'll find on the [www.lesswatts.org](www.lesswatts.org) page actually.   Another thing that is helpful is to figure out what it is thats writing to your hard drive.

thats about it...any questions just ask.

---

