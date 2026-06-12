---
title: "undervolting AMD Turion using cpupowerd"
date: 2008-07-07
forum: Hardware
---

### Post by balak on 2008-07-07
Hi Everybody,

I am trying to reduce the temperature of my laptop using undervolting.
I have an AMD Turion 64 MT-28 processor running Hardy 8.04 amd64 version (fully updated).

I found this cool program in a german ubuntu/linux forum called 'cpupowerd' 

[http://sourceforge.net/projects/cpupowerd](http://sourceforge.net/projects/cpupowerd)

It first reads your current fid/vid (frequency/voltage id) programming and allows you to reduce the cpu voltage at a certain frequency. 

Unfortunately, I don't understand german and google translation didn't help me understand how to set and run this all the time either.

For those of you who want to try it out: please note that this program can easily damage your cpu/system if you mix up the settings.

However, I am having issues with turning off powernowd which controls the frequency variation in hardy by default. I have tried /etc/init.d/powernowd stop which turns this off by I still get powernow-k8 messages in dmesg log. 

If I start cpupowerd when powernowd is running, the undervolting is overriden by powernowd

Any ideas on how to proceed?

thanks!

---

### Post by smax3 on 2008-07-09
Hello balak,

I am the developer from cpupowerd.
I think your problem isn't the powernowd, because you have it stopped with "/etc/init.d/powernowd stop".
Sometimes the Gnome-Power-Manager make troubles on cpu undervolting, so test to stop or kill the gnome-power-manager and try cpupowerd again.

---

### Post by balak on 2008-07-10
Thanks smax!

I was hoping that you'll respond to this thread ;) you have written a very cool program - thanks again!

So I killed gnome-power-manager, stopped powernowd and started cpupowerd

cpupowerd -d -c /etc/cpupowerd.conf

```
$ more /etc/cpupowerd.conf 
800 0.8750
1600 1.0750

```

However, if I check back the voltage, it still shows the old voltage:

```
$$sudo cpupowerd -s
cpupowerd 0.1.2
WARNING: This program could cause damage to your Hardware!

Physical cpu                  : 0
  Vendor                      : AMD
  Family                      : 1
  Model                       : 2
  Coreids                     : 0
    Mastercoreid              : 0
      Affected coreids        : 0
      Current voltage (VID)   : 1.0500 V (20)
      Current frequency (FID) : 800 MHz (0)
      Supported frequencies   : 800 1600 MHz

```

Am I doing anything wrong in this?

thanks!

---

### Post by smax3 on 2008-07-10
Hello balak,

first, please remove my mailadress from the output of cpupowerd -s ;).

Can you try "cpupowerd -f -c /etc/cpupowerd.conf", create cpu load with the script createload.sh included in cpupowerd package (don' forget to read the README-File) and send me the output over mail?

---

### Post by balak on 2008-07-10
I have attached the two files. one is the output of cpupowerd in foreground mode and the other is the output of mprime stress test.

---

### Post by balak on 2008-07-14
Finally, I figure out one way, thanks to smax.
There is hal, addon process called 'hald-addon-cpufreq' which is started in hald. It doesn't let cpupowerd do its job. Once you kill that process and then run cpupowerd, it works like a charm.

My laptop used to run at 53-55C all the time and now its mostly running at 45C.

---

### Post by jimv on 2008-07-14
I don't know if it's really necessary to mess with your voltages and all that.  I use the CPU Frequency Scaling panel app to throttle my processor and I get the temp from 55 down to about 40.

---

### Post by balak on 2008-07-14
> **jimv said:**
> I don't know if it's really necessary to mess with your voltages and all that.  I use the CPU Frequency Scaling panel app to throttle my processor and I get the temp from 55 down to about 40.

I agree. It is not at all required and probably not advisable to do that. But I just wanted to try and see what gains I can get.

---

### Post by smax3 on 2008-07-15
> **jimv said:**
> I don't know if it's really necessary to mess with your voltages and all that.  I use the CPU Frequency Scaling panel app to throttle my processor and I get the temp from 55 down to about 40.

I don't agree ;).
CPU throttling is normaly used, when the cpu is in idle mode to get lower frequencies as over Cool'nQuiet/EIST.
The temp and noise in cpu-idle-mode is not a problem in the most cases.
But on full-cpu-load, the temp is much higher and the fan is very loud! Here undervolting can help to reduce the temp and noise.

What's on desktop systems?
My desktop amd64 x2 3800+ ee sff system haven't a throttling mode (only Cool'nQuiet). Here is undervolting the only possibility way to reduce the power usage (and the noise). My desktop system needs less **20W** in idle-mode with cpu undervolting (see [here]("http://www.meisterkuehler.de/forum/vorstellung-von-stromspar-pcs/16008-stromspar-rechner-mit-amd-x2-3800-ee-sff-sind-idlewerte-unter-17-watt-moeglich.html")).

---

### Post by jimv on 2008-07-15
Ah, I see.  By throttle, I mean I set my CPU speed to about 1/3 of what it normally is, which is more than enough for most of what I do.

I use a cheapo Gateway laptop that seems to get too hot (for some reason the GPU is always running around 70C in any OS)

---

### Post by smax3 on 2008-07-15
> **jimv said:**
> By throttle, I mean I set my CPU speed to about 1/3 of what it normally is

Ooops, throttle and throttling are different :).

With cpupowerd (or powernowd, cpufreqd, ...) the throttle will be done automatically depended from cpu load.

---

### Post by jimv on 2008-07-15
It does do it automatically, but it doesn't keep things very cool in my case.  SO I adjust it manually.

---

### Post by mk_cafe on 2008-08-31
can i use this program when my acpi is turned off (i can't boot ubuntu any way when turned acpi on)?

---

### Post by Lonthong on 2008-09-07
Hello, 
I am running Hardy 64 bit & Windows Xp on my laptop BenQ P41 (turion X2 TL 50, Radeon X1100)
I am using RMclock with the following setting:
FID=4.0 VID=0.725
FID=5.0 VID=0.775
FID=6.0 VID=0.825
FID=7.0 VID=0.850
FID=8.0 VID=0.900

I just installed & ran cpupowerd -s:
cpupowerd 0.1.2

WARNING: This program could cause damage to your Hardware!



Physical cpu                  : 0

  Vendor                      : AMD

  Family                      : 1

  Model                       : 4

  Coreids                     : 0 1

    Mastercoreid              : 0

      Affected coreids        : 0 1

      Current voltage (VID)   : 1.0750 V (19)

      Current frequency (FID) : 1600 MHz (8)

      Supported frequencies   : 800 1600 MHz

My question: Do I have to adjust VID for only 800MHz & 1600MHz & the program will auto create all in between VID value - like RM Clock did or do I have to do it manually & is this ok since it said only 2 supported frequencies 800 & 1600 MHz??

Finally how you kill "hald-addon-cpufreq"?
as for killing gnome-power-management, I just untick it from system - preference- sessions.

---

### Post by smax3 on 2008-09-08
> **mk_cafe said:**
> can i use this program when my acpi is turned off (i can't boot ubuntu any way when turned acpi on)?
I haven't tested the program with acpi is turned off, but I think it doesn't work.
Boot your system an check if /sys/devices/system/cpu/cpu0/cpufreq/ is available.
On my system it looks like:
```
/sys/devices/system/cpu/cpu0/cpufreq$ ls -la
insgesamt 0
drwxr-xr-x 4 root root    0 2008-09-08 10:49 .
drwxr-xr-x 5 root root    0 2008-09-08 10:49 ..
-r--r--r-- 1 root root 4096 2008-09-08 10:49 affected_cpus
-r-------- 1 root root 4096 2008-09-08 10:49 cpuinfo_cur_freq
-r--r--r-- 1 root root 4096 2008-09-08 10:49 cpuinfo_max_freq
-r--r--r-- 1 root root 4096 2008-09-08 10:49 cpuinfo_min_freq
drwxr-xr-x 2 root root    0 2008-09-08 10:49 ondemand
-r--r--r-- 1 root root 4096 2008-09-08 10:49 scaling_available_frequencies
-r--r--r-- 1 root root 4096 2008-09-08 10:49 scaling_available_governors
-r--r--r-- 1 root root 4096 2008-09-08 10:49 scaling_cur_freq
-r--r--r-- 1 root root 4096 2008-09-08 10:49 scaling_driver
-rw-r--r-- 1 root root    0 2008-09-08 10:49 scaling_governor
-rw-r--r-- 1 root root 4096 2008-09-08 10:49 scaling_max_freq
-rw-r--r-- 1 root root 4096 2008-09-08 10:49 scaling_min_freq
drwxr-xr-x 2 root root    0 2008-09-08 10:49 stats

```

> **Lonthong said:**
> My question: Do I have to adjust VID for only 800MHz & 1600MHz & the program will auto create all in between VID value - like RM Clock did or do I have to do it manually & is this ok since it said only 2 supported frequencies 800 & 1600 MHz??
Yet, cpupowerd supports **only** the "cool and quiet" frequencies - in your case 800 and 1600 MHz and no between frequencies will be used (and is not allowed!).
In my opinion it does **not** really make sense to use every possible frequency steps on the cpu, because the time to get full cpu-power is longer than you use less frequencies. In some less situations it make sense  (e.g. you want to use 1400MHz instead of 1600MHz) and so this feature have low priority (but is on the todo list :)) and will be implemented in the future.

---

### Post by Lonthong on 2008-09-08
Thank you for your kind reply. Meanwhile I have been playing around with yr program....

I set my cpupowerd.conf as follows:
800 0.7250
1600 0.9000
and sudo cpupowerd -d -c cpupowerd.conf 
then sudo cpupowerd -s gave me:
cpupowerd 0.1.2
WARNING: This program could cause damage to your Hardware!
Written by

Physical cpu                  : 0
  Vendor                      : AMD
  Family                      : 1
  Model                       : 4
  Coreids                     : 0 1
    Mastercoreid              : 0
      Affected coreids        : 0 1
      Current voltage (VID)   : 0.7250 V (35)
      Current frequency (FID) : 800 MHz (0)
      Supported frequencies   : 800 1600 MHz

By the way I tried with both gnome-power-management on and off but the result is always the same as above (ticking and unticking the appropriate entry in system - preference - sessions) and moreover I don't kill hald-addon-cpufreq (in fact I don't know howto kill it). 
So for now I just leave gnome-power-management on....

My question now, how to make it start-up automatically?
Right now everytime I have to:
modprobe msr
cpupowerd -d -c cpupowerd.conf 

Also how do I know whether my cpu is throttling? I don't want it to run at 800MHz only......

---

### Post by smax3 on 2008-09-09
> **Lonthong said:**
> My question now, how to make it start-up automatically?
Right now everytime I have to:
modprobe msr
cpupowerd -d -c cpupowerd.conf
[Here]("http://www.silentpcreview.com/forums/viewtopic.php?p=427710#428506") ([http://www.silentpcreview.com/forums/viewtopic.php?p=427710#428506](http://www.silentpcreview.com/forums/viewtopic.php?p=427710#428506)) is a description how you can start cpupowerd automatically.

> **Lonthong said:**
> Also how do I know whether my cpu is throttling? I don't want it to run at 800MHz only......
Read the included README file and look at chapter STRATEGIES and TEST PROCEDURE.
Test cpu-voltage-stability and frequency changing with mprime.
For a short test use e.g. "cat /dev/urandom > /dev/null" in a terminal.
Check in a other terminal with "sudo cpupowerd -s" the cpu state.

---

### Post by Lonthong on 2008-09-09
Thanks, everything is now working perfectly.

Edit.
Well, not perfectly yet.....
Everytime I hit log off, the system freeze for a couple of minutes & moreover there is no more suspend & hybernation button.
THis also happened when I still manually set cpupowerd. It will be back to normal again as soon as I re-activate gnome-power-management
Edit2.
Strange, it happened only at random. Sometimes, everything just works normally..........

---

### Post by BillyBuerger on 2008-09-29
I just loaded up ubuntu on a PC with a Turion CPU on a standard desktop motherbord.  (Soltek SL-K8AN2E-GR)  Powernowd wasn't working and cpupowerd sounded better.  Powernowd tells me "CPU frequency scaling not supported..."  cpupowerd tells me "Can't open /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor for reading!"  The motherboard itself doesn't recognize the CPU and lists it as an unknown Hammer CPU.  Does this mean I'm screwed for using any power states in Linux?

I had windows loaded previously.  Windows would just leave it at 800MHz and never clock up on it's own.  But with RMClock, I was able to adjust the states and run it just like any other desktop CPU.  I'm planning on using it for a simple file server and some simple php/mysql stuff.  So I may just hard-wire it to 800MHz@0.8V in the BIOS which works fine.  But it would be nice to have the extra power when needed.  It's replacing a 600MHz celeron which uses very little power but is a bit slow.

---

### Post by 444 on 2008-10-06
> **BillyBuerger said:**
> The motherboard itself doesn't recognize the CPU and lists it as an unknown Hammer CPU.

The way things work is that the motherboard mfg programs all the speed-voltage combinations into the BIOS acpi table (hint: BIOS update may help). So if the BIOS does not recognize the CPU, then all the standard CnQ drivers for windows or linux (RMClock isn't standard...) end up not working.

As far as I can tell (didn't look closely) cpupowerd relies on the CPU being recognized by the BIOS, then replacing the voltage values given by the BIOS. Thus it will not work in this case.

There is the program k8fq, which allows you to enter any speed/voltage combination regardless of what the BIOS says. Unfortunately you have to switch speeds manually unlike RMClock.

---

### Post by bluebear on 2008-10-15
SMAX3 thanks for a really nice program! 
I´m doing my best spreading the word around. The only wish now is for underclocking as well. That would be supernice. 
Thanks again!

---

### Post by smax3 on 2008-11-02
Today, cpupowerd 0.2.0 was released.

A start script for linux is now available.
For more details read the CHANGELOG and README files.

Download cpupowerd under [sorceforge]("http://sourceforge.net/project/showfiles.php?group_id=227607").

---

### Post by quazar on 2008-12-27
I have been struggeling getting cpupowerd to work, these tips might be useful for newbies like me :)

First install cpupowerd according to the readme file

- make the modules msr, cpufreq_userspace, and powernow-k8 start at bootup, otherwise cpupowerd wont work:

$ sudo gedit /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

[COLOR="Gray"]fuse
lp
rtc[/COLOR]
msr
cpufreq_userspace
powernow-k8
```

after a reboot cpupowerd should work, to test this type:
```
$sudo cpupowerd -s
``` 

- to get cpupowerd to run from startup, the script cpupowerd.sh (in the tools folder) needs to e run at start-up.
1) edit the script if your cupowerd.conf file is not located at /etc/cpupowerd.conf 
 change the line accordingly:
```
"CPUPOWERD_STARTPARAMETERS="-d -c /etc/cpupowerd.conf"
```
2) copy the script to the folder etc/init.d/ directory
3) activate the script:
```
sudo update-rc.d cpupowerd.sh defaults 
sudo chmod +x cpupowerd.sh
```

---

### Post by Lockheed on 2009-05-15
I'm trying to run this program but all I get is 

```
WARNING: This program could cause damage to your Hardware!
MSR-File </dev/cpu/0/msr> doesn't exist, please load the msr kernel module!
Initialisation failed!
```

How do I install this? It is nowhere in Synaptic.

---

### Post by matthewbpt on 2009-05-18
> **Lockheed said:**
> I'm trying to run this program but all I get is 

```
WARNING: This program could cause damage to your Hardware!
MSR-File </dev/cpu/0/msr> doesn't exist, please load the msr kernel module!
Initialisation failed!
```

How do I install this? It is nowhere in Synaptic.

Try running

```
sudo modprobe msr
```

then run cpupowerd again

-matt

---

### Post by Lockheed on 2009-05-24
Great! I got everything working now with the help of this HOWTO: [http://www.silentpcreview.com/forums/viewtopic.php?p=427710#428506](http://www.silentpcreview.com/forums/viewtopic.php?p=427710#428506)

Still, it would be even better if intermediary frequencies worked.

---

### Post by Lockheed on 2009-06-02
I though I had it but I guess I don't.

powercpud behaves erratic. If computer iddles everything is fine, the voltage is just as I set it. However, if there is some heavy load there are two high frequency voltage scenarios that happen just equally often:

1. the voltage I set (0.9v)
2. the stock voltage (1.1v)

Now, what I say is not confirmed and it just my gut feeling:if the load is heavier than, say 80%, the voltage for 1600Mhz goes to 1.1. If it is lower, 1600Mhz stays at 0.9v.

I have no idea why. Any ideas?

---

### Post by hegoburu on 2009-07-28
i have a question... i have a AMD Turion X2 running jaunty 64 bits... and when running cpupowerd i get 

Your AMD CPU isn't supported yet (cpuid: 0x200F31)!
Initialisation failed!

Is there anything to be done or i am busted until it is supported? 

Thanks!!

---

### Post by nema.arpit on 2009-08-02
There are no modules for cpufreq or powernow-k8.. how do I get them?

```

arpit@arpit-laptop:~$ sudo modprobe cpufreq
**WARNING**: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
**WARNING**: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
**FATAL: Module cpufreq not found.**
arpit@arpit-laptop:~$ sudo modprobe powernow-k8
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
**FATAL: Module powernow_k8 not found.**

```My kernel is 2.6.28.14,running Jaunty 64bit AMD Turion X2 rm-72.
Current power management using kpowersave.
Oh and how do i measure the temperatures .. I tried xsensors but it does not work.

ps. any ideas about those warnings?

---

### Post by jasmineaura on 2009-08-02
> **nema.arpit said:**
> There are no modules for cpufreq or powernow-k8.. how do I get them?
My kernel is 2.6.28.14,running Jaunty 64bit AMD Turion X2 rm-72.
Current power management using kpowersave.
Oh and how do i measure the temperatures .. I tried xsensors but it does not work.

ps. any ideas about those warnings?

The stock "generic" kernel has all these compiled into the kernel, and not as modules, so if you need them as modules instead of compiled in the kernel (as required by another tool: linux-phc.org) then you have to reconfigure and compile the kernel from kernel sources....

```
sudo apt-get install linux-source-`uname -r`
```

Add your username to the "src" group:
```
usermod -a -G src yourusername
```

then:

```

cd /usr/src
tar xzf linux-source-`uname -r`.tar.gz
cd linux-source-`uname -r`
make menuconfig

```

Then in menuconfig, go to:
Power management and ACPI options  --->
enable the following menu/item (CONFIG_CPU_FREQ=y) and enter it:
CPU Frequency scaling  --->

Make sure you choose as module (Marked as [M]) at least the following:
powernow-k8
freq-table
 cpufreq-stats
cpufreq-userspace
cpufreq-conservative
cpufreq-ondemand
cpufreq-powersave

Then build your kernel and prepare a .deb of your newly compiled kernel with 
```
fakeroot make-kpkg --initrd --append-to-version=-custom1 --revision=1.0 kernel-image kernel-headers

```then install the linux-image and linux-headers packages created in the top directory (/usr/src typically)
```
cd ..
sudo dpkg -i *.deb

```For brief tutorial, see:
[http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67)

Edit:
for the temperatures monitoring, I use sensors-applet in gnome (easily added to the panel by right clicking and click Add to Panel), then right click the newly added sensors-applet and click preferences, go to sensors tab, expand "libsensors" category and choose your CPU and cores (check them), and you can also expand "nvidia" if you're running the proprietary nvidia driver and check your GPU as well to monitor its temperature too..

good luck

---

### Post by Defrector on 2009-08-12
The most recent issue above confused me, as I am using 9.04 and have no problems with cpupowerd. However when I run those above commands the same error happens so I don't think this is really the issue at all.

I recommend adding those module names into /etc/modules and rebooting. This works for me.

---

### Post by ttanev on 2010-07-17
```
cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
Your AMD CPU isn't supported yet (cpuid: 0x200F31)!
Initialisation failed!
```:(

AMD Athlon QL-62 on a Asus M51TR notebook.

---

### Post by cardonarico on 2010-07-30
Same here 

cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
Your AMD CPU isn't supported yet (cpuid: 0x200F31)!
Initialisation failed!


I would love to get a new cpupowerd version supporting newer CPUs.

I am running an HP2510us notebook with serious thermal problems and undervoltage it could be an awesome option.

I hope the developer still reads the forum and or is working on a newer version.

---

### Post by vozmem on 2010-10-17
[SIZE="3"][COLOR="Green"]I hate to say this but I cannot load the cpufreq_userspace and powernow_k8 modules on Ubuntu 10.10. Help me, bro.[/COLOR][/SIZE]

---

### Post by hodginsa on 2011-01-09
I have just finished an install of ubuntu 10.10 on my HP L2000 laptop. I'm am in the process of getting it to run lower voltages since the ml-32 is overvoltaged right from the get go!

I'm very new to Ubuntu, but I think I have installed everything correctly so far. 

I want to run the voltages as follows:
800MHz @ .8750
1600MHz @ 1.0750
1800MHz @ 1.35 (recommended by AMD)

The issue is when I have cpupowerd running it won't let me switch to 1800MHz cause it says invalid frequency, it switches back to 800MHz. After a few seconds it goes back to the original voltages set by the system. I believe I cancelled everything that would make it go back. I'm confused.

---

