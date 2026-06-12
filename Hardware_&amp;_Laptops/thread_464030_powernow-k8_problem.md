---
title: "powernow-k8 problem?"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by D!mon on 2007-06-04
I have strange problem: last time I was running Folding@Home application on my computer before when I had Edgy installed on it.
Then I upgraded to Feisty with the release and started the folding today in the morning. After some time I noticed that it performs very slow (~1% in an hour, that took about 23 minutes in the past). Then I noticed that my computer is very cool like it doesn't run at 100% CPU and - what you think - it actually doesn't! The top command reports 100% CPU usage (and it actually is 100%) but CPU frequency applet shows only 1Ghz frequency instead of 2.20Ghz, so for some reason my CPU works like there is no F@H running. I even tried changing the nice of FahCore process from 19 to 0 but it didn't change anything. I have AMD X2 4200+ CPU and can provide any logs if needed. Is it powernow-k8 problem or F@H application problem and what can I do?
I also posted this problem to F@H thread.
Thanks

---

### Post by D!mon on 2007-06-04
Update: 
cpufreq-info reports a correct limits:
```

dimon@dimon-desktop:~$ sudo invoke-rc.d powernowd start
 * Starting powernowd...                                                 [ OK ] 
dimon@dimon-desktop:~$ sudo cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).

```

but f@h starts working just like before after I stop powernow:
```

dimon@dimon-desktop:~$ sudo invoke-rc.d powernowd stop
 * Stopping powernowd:                                                   [ OK ] 
dimon@dimon-desktop:~$ sudo cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.20 GHz (asserted by call to hardware).
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.20 GHz (asserted by call to hardware).

```

Actually it seems that f@h uses the current value of cpu freq and can't scale it up for some reason; but it worked fine with edgy anyway. Is it a bug or feature?
So I am able to run powernow if I set governor to performance with cpufreq-set.. but as i remember it worked fine with ondemand before.

---

### Post by jpkotta on 2007-06-04
It seems like it does what you want when powernowd is stopped, so why not just keep it off?  Or are you just curious as to why the behavior is changed?

---

### Post by D!mon on 2007-06-04
Yes, and i'm not sure that this new behaviour is correct. If I have governer called 'on demand' turned on I want it to scale the cpu up for programs like f@h and i don't know why it doesn't, especially if before it did.
Btw, I can keep powernow turned on if I set governor to performance with cpufreq-set

---

### Post by jpkotta on 2007-06-04
It might have something to do with how powernowd treats nice'd processes, but you've already tried setting the nice to 0.  

I think a more likely explanation is that powernowd and the kernel frequency governor are fighting for control.  See if the kernel module is loaded with lsmod.  I'm not sure exactly how to two are related (are they independent or does powernowd use the module?), but if I had to guess, I'll bet the kernel governor needs to be set to userspace in order for powernowd to work.  Also, I think the cpu-freq-utils only interact with the module.

---

### Post by D!mon on 2007-06-05
Here is my lsmod output: 
```

dimon@dimon-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            14604  1 
powernow_k8            16480  1 
cpufreq_userspace       6176  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10640  0 
freq_table              6336  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
dev_acpi               17028  0 
sony_acpi               7064  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
dock                   11992  0 
button                 10016  0 
battery                12040  0 
container               6144  0 
ac                      6920  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
af_packet              27020  0 
fuse                   51888  1 
lp                     15048  0 
snd_hda_intel          24224  5 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm_oss            49536  0 
snd_pcm                92808  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          19840  1 snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               8107320  44 
snd                    68904  18 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
parport_pc             40104  1 
parport                43404  2 lp,parport_pc
k8temp                  7552  0 
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm
psmouse                43536  0 
serio_raw               9092  0 
pcspkr                  4736  0 
i2c_nforce2             7680  0 
i2c_core               26496  3 i2c_ec,nvidia,i2c_nforce2
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
ipv6                  307456  10 
evdev                  13056  3 
tsdev                  10112  0 
ext3                  143760  2 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
sd_mod                 25092  3 
sata_nv                24196  3 
usbhid                 29088  0 
hid                    34048  1 usbhid
ata_generic            10628  0 
amd74xx                16944  0 [permanent]
ehci_hcd               37004  0 
forcedeth              48776  0 
ohci_hcd               24196  0 
libata                137000  2 sata_nv,ata_generic
scsi_mod              166968  3 sg,sd_mod,libata
generic                 6532  0 [permanent]
usbcore               154416  4 usbhid,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  2 powernow_k8,thermal
fan                     6536  0 
capability              7048  0 
commoncap               9472  1 capability
vesafb                 10376  1 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
fbcon                  44416  72 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit

```

So how can I set governor to user mode if that is required? And why it worked just fine before the upgrade to feisty?

---

### Post by jpkotta on 2007-06-05
Like I said, the cpufreq-utils (like cpufreq-set) deal with the kernel module.  Use ```
cpufreq-set -g userspace
```
to set the kernel module for userspace control.

The difference between edgy and feisty is that the kernel module is used by default instead of powernowd.  There is an entry in the F@H wiki page about this.  

The weird thing is that I had the opposite problem when I installed Feisty.  I don't want my laptop to kick up the freq just for F@H, but that behavior changed because of different (and IMO, bad) defaults in the kernel module vs. powernowd.  

If I was you, I would forget about governors all together, because you want to run at max freq when you run F@H, and presumably you are running F@H all the time, so why not just fix the frequency and be done with it?  Uninstall powernowd, set the min and max freqs with cpufreq-set, and add a command in /etc/rc.local to do it at boot time.

---

### Post by D!mon on 2007-06-05
yeah, maybe you re right, actually I just want to work out the 'correct' way of fixing the problem, but I already thought about what you suggested and most likely will do it that way, though I'm not happy with all those kernel problems around there :(

---

### Post by jpkotta on 2007-06-05
But if you don't want the frequency to change, then using a governor is the incorrect solution, because they are designed to change the frequency.  But if you insist on using a governor, it really doesn't matter whether you use powernowd or a different daemon or the kernel module.  All you have to do is make sure only one is running, and then learn how to configure it.  I would recommend using the kernel one, because it's easy to uninstall powernowd and be sure it's not there.

[QUOTE=linux/Documentation/cpu-freq/user-guide.txt]
    110 2.1 Policy
    111 ----------
    112 
    113 On these systems, all you can do is select the lower and upper
    114 frequency limit as well as whether you want more aggressive
    115 power-saving or more instantly available processing power.
    116 
    117 
    118 2.2 Governor
    119 ------------
    120 
    121 On all other cpufreq implementations, these boundaries still need to
    122 be set. Then, a "governor" must be selected. Such a "governor" decides
    123 what speed the processor shall run within the boundaries. One such
    124 "governor" is the "userspace" governor. This one allows the user - or
    125 a yet-to-implement userspace program - to decide what specific speed
    126 the processor shall run at.
    127 
    128 
    129 3. How to change the CPU cpufreq policy and/or speed
    130 ====================================================
    131 
    132 3.1 Preferred Interface: sysfs
    133 ------------------------------
    134 
    135 The preferred interface is located in the sysfs filesystem. If you
    136 mounted it at /sys, the cpufreq interface is located in a subdirectory
    137 "cpufreq" within the cpu-device directory
    138 (e.g. /sys/devices/system/cpu/cpu0/cpufreq/ for the first CPU).
    139 
    140 cpuinfo_min_freq :              this file shows the minimum operating
    141                                 frequency the processor can run at(in kHz) 
    142 cpuinfo_max_freq :              this file shows the maximum operating
    143                                 frequency the processor can run at(in kHz) 
    144 scaling_driver :                this file shows what cpufreq driver is
    145                                 used to set the frequency on this CPU
    146 
    147 scaling_available_governors :   this file shows the CPUfreq governors
    148                                 available in this kernel. You can see the
    149                                 currently activated governor in
    150 
    151 scaling_governor,               and by "echoing" the name of another
    152                                 governor you can change it. Please note
    153                                 that some governors won't load - they only
    154                                 work on some specific architectures or
    155                                 processors.
    156 scaling_min_freq and
    157 scaling_max_freq                show the current "policy limits" (in
    158                                 kHz). By echoing new values into these
    159                                 files, you can change these limits.
    160                                 NOTE: when setting a policy you need to
    161                                 first set scaling_max_freq, then
    162                                 scaling_min_freq.
    163 
    164 
    165 If you have selected the "userspace" governor which allows you to
    166 set the CPU operating frequency to a specific value, you can read out
    167 the current frequency in
    168 
    169 scaling_setspeed.               By "echoing" a new frequency into this
    170                                 you can change the speed of the CPU,
    171                                 but only within the limits of
    172                                 scaling_min_freq and scaling_max_freq.
[/QUOTE]

---

### Post by tintax on 2007-06-17
PowerNowd ignores "niced" programs by default when calculating the CPU load. According to the developer "this is consistent with what is meant when someone 'nice's a program to begin with". However this behaviour is configurable: passing the -n option to powernowd will include those processes in the calculations.

Hope this helps. More information is available at the program's [homepage]("http://www.deater.net/john/powernowd.html").

---

