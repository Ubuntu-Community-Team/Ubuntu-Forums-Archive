---
title: "Pentium M 725 (Dothan 1.6) Only 2 scaling levels?"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by DustoneGT on 2006-07-20
I have a gateway 3522gz, with the pentium m 725 processor.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
gives me
1600000 600000

The CPU frequency scaling applet gives me the same thing, only
600mhz or 1.6ghz.

When I used to run windows last year on this thing it would give me
as low as 20mhz and many more steps in-between up to the full throttle.

The concensus of everything I read is that 600mhz is the minimum and
the windows program was giving me bogus low readings, however I would
like to know if there is any way I can get more steps between lowest
supported speed and highest.

Can I get some more steps enabled somehow?  I would think I could potentially save some battery life if it didn't have to go as high as
1.6 all the time.

Any help greatly appreciated.

---

### Post by matthew on 2006-07-20
I have a Pentium M 745 (Dothan 1.8 ). Here is the output on mine for comparison.```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1800000 1600000 1400000 1200000 1000000 800000 600000
```I have not done anything special to my installation to enable this so I am not sure what you need to do, but at least I can confirm you can get at least as many as 7 different steps in a sister CPU.

Is powernowd installed? Is it running?

It is configurable, but I'm not very experienced with doing that (mine was configured perfectly out of the box...) Try "man powernowd" for the options. I know you can create a config file for the daemon at /etc/default/powernowd with a line like```
OPTIONS="-q -m 2"
``` in it.

---

### Post by DustoneGT on 2006-07-20
powernowd is installed and running....
I played with the options listed in man powernowd
and it seems to be a slave to the options in
scaling_available_frequencies.....

I tried to edit that file and it gives me access denied....

With you getting those 7 levels I am confused...

---

### Post by mpvano on 2006-07-20
My Pentium M shows only 1.20 Ghz and 2.0 Ghz and switches dynamically between the two of them as required.

Like you, I spent a lot of time trying to figure out how to get more steps because I hoped it would improve the battery life.

I learned that there is more than one choice of cpu speed governer module which would work with my machine, and that the one that was chosen by the Ubuntu installation was called "speedstep-ich", and that's what is setting this two step behavior.

It's hard to switch governer drivers after boot. The driver is normally loaded in Dapper by the "powernowd" Daemon startup script. Like many other daemons, it's configured by a file in /etc/default called "powernowd".

On my machine, I can put one of the following two lines into this file (there's no FREQDRIVER line in the default file - this loads speedstep-ich)

FREQDRIVER="p4-clockmod"

FREQDRIVER="acpi-cpufreq"


You can (via sudo) edit this file to add one or the other of these  and then restart if you want to experiment. The one called "p4-clockmod" has fine grained behavior like you are describing and goes from 250mhz to 2.0ghz in many steps on my machine.

I found that using this governer didn't really save any appreciable amount of power, but that it made the machine very unresponsive. The entire system is controlled by "files" in /sys/devices/cpu/CPU0/cpufreq and the subdirectories there. You can see tha available choices for all the speed control options there and even directly manipulate them using sudo.

There are some comments in the kernel documentation that indicate that there's no point in using p4-clockmod as it slows the machine down a lot, but doesn't save any more power than speedstep-ich. I found this to be true myself. After a month of experiments switching governers, and manually controlling the speed (where applicable) via the "files" in /sys/, I went back to just using speedstep-ich with powernowd's default settings. The machine is quite responsive using it and I found the only way to keep the machine responsive using p4-clockmod was to set the minimum frequency quite high (at least 500mhz), which ended up using as much power as the speedstep module 1.25 mhz settings.

I suggest studying the man pages and documentation in /usr/share/doc for powernow and all the /sys files and configuration files involved. The system is quite elaborate, but easy to use. However you can get very confused by the fact that some governers have built in control that can't be modified outside the kernel, and others are controlled by a userspace daemon (like powernow). Powernow may THINK it's controlling some governers, but they actually ignore any input from user space.

You can just try switching to p4-clockmod by the entry described above in /etc/default/powernowd and see if you like the behavior. If it show's promise, run some tests of your own. As I say, however, I ended up happiest with the original defaults as shipped...

By the way, laptop mode made more difference than anything else on my machine in saving power. It's disabled by default, you might read its documentation and then consider trying it if your machine is working stably. (otherwise there's a slight chance it could cause data loss if your machine crashes with the a lot of unwritten data in the disk buffersl) It's enabled in /etc/default/acpi-support by uncommenting the line at the end of the file. It works well for most people.

On my particular machine (IBM T30), there was originally a bug in the video drivers that caused hangups if the acpi system was allowed to shut down the pci bus interface for the video card to save power. The current drivers don't have this problem, so adding the line

        Option          "DynamicClocks" "On"

to the radeon device section for my particular ATI card (ONLY!) also made quite a difference, but I think that's unique to the IBM T30. Don't try it unless you use the "ati" or "radeon" ATI driver and know how to recover if X windows won't start.

Hope this points you to some useful information. Be careful not to do anything you don't know how to recover from, however....

Mario

---

