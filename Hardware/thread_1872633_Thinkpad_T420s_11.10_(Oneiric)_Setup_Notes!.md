---
title: "Thinkpad T420s 11.10 (Oneiric) Setup Notes!"
date: 2011-10-31
forum: Hardware
---

### Post by junkilo on 2011-10-31
Sharing my setup notes on a T420s i7-ssd. This also is mostly applicable to most thinkpads in the T400 line, like the T410 and T420.

Ubuntu 11.10 (64bit) is fantastic. To get better battery life it needed a few kernel features enabled, fan control to be optimized and video drivers updated. The 3.0 kernel might enable more power saving features in the future, but I'm pretty happy at the moment on 3.0.0.12.

According to powertop with chrome and terminal running on wireless (intel graphis only) I'm drawing around 8w with brightness around 3/4 of the way. Power consumption goes up to 10w on full brightness. The stock 6 cell battery does a max of about 5.5 hours when drawing around 8w and around 4 hours when drawing around 10w according to the battery estimates. 

When I started the system was using around 21w with the same work loads. With the tweaks and using the nvidia graphics its using around 21w. 

There are more tweaks I could do (pm-powersave, tweak thinkfan and tlp more, set other hardware to turn off, etc) but I don't have much need.

Thanks to others who have posted and shared infos on these forums.

Setup summary:


[LIST=1]updated the bios to latest (v1.29)
[*]set bios to use just one video card
[*]installed ubuntu 11.10 64 bit and run all updates
[*]added a bunch of repos: mediabuntu, restricted, universe, etc
[*]add special repos:
```
apt-get-repository ppa:linrunner/tlp
apt-get-repository ppa:oibaf/graphics-drivers
apt-get-repository ppa:ubuntu-x-swat/x-updates
```
[*]install goodies
```
apt-get install thinkfan tlp ethtool smartmontool tp-smapi-dkms powertop lm-sensors nvidia-settings nvidia-current
```
[*]rerun updates ```
 apt-get update && apt-get dist-upgrade
```
[*]reboot
[*]enable power saving render, active state power mgmt: in /etc/default/grub ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"
```
[*]update grub ```
 update-grub
```
[*]reboot
[*]update sensors from lm-sensors ```
sensors-detect
```
[*]enable thinkfan in /etc/defaults/thinkfan ```
START=yes
```
[*]enable acpi fan: ```
echo "options thinkpad_acpi fan_control=1" >>/etc/modprobe.d/thinkpad_acpi.conf
```
[*]configure thinkfan in /etc/thinkfan.conf ```
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
```
[*]fix a sound problem when docked: ```
echo "options snd-hda-intel model=thinkpad" >> /etc/modprobe.d/alsa-base.conf
```
[*]enable tlp: /etc/defaults/tlp ```
 TLP_ENABLE=1
```

[/LIST]




References:
[http://ubuntuforums.org/showthread.php?p=11379221](http://ubuntuforums.org/showthread.php?p=11379221)
[http://thinkpad-wiki.org/Thinkfan](http://thinkpad-wiki.org/Thinkfan) 
[http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

---

### Post by steevven1 on 2011-10-31
Virtually all of your power savings are coming from this kernel parameter: i915.i915_enable_rc6=1

This parameter is known to cause graphical glitches and system freezes on Sandy Bridge processors, just so you know. Are you experiencing any problems like this?

On my ThinkPad X220 (also with a Sandy Bridge i7), this kernel parameter causes HUGE power savings and also graphical glitches and freezes.

---

### Post by UberSteve on 2011-11-12
Hi junkilo,

Thanks for your post! Unforunately, my install hasn't gone smooth.

I've got a T420s (4170-CTO) configured with nVidia Optimus.

After a fresh install of 11.10 64-bit, the machine freezes on a purple screen. From what I can tell, it's freezing at the point of starting X. I've booted recovery mode, and there are no obvious errors.

The Ubuntu 11.10 64bit Live CD has no troubles booting.

I'm pretty sure it's somehow related to uefi and/or the nvidia gpu.

After a lot of stuffing about, the only way to get it boot is to add the "noapic" option to grub. But i'm not sure if this is the correct solution, and I would like to understand why the APIC needs to be disabled?

Did you strike this problem by any chance? I was wondering if you could confirm the following BIOS settings for me? (My current settings are in [] and these are the settings I installed Ubuntu with)
-Config->Display-Graphics Device [Discrete Graphics]
-Config->Display-OS Detection for NVIDIA Optimus [Disabled]
-Startup->UEFI/Legacy Boot [UEFI Only]
-Startup->UEFI/Legacy Boot Priority [N/A]

TIA!

-Steve

---

### Post by Astronaut356 on 2011-11-13
I'm very interested in following this thread. I ordered a T420s with Core i5 and the Intel HD 3000 graphics. (My ship date is 11/29, even though I ordered it on 11/4. I don't know why Lenovo takes an eternity to ship their laptops when Apple makes theirs in China too and can ship in 3 days. But I digress...) I am planning on installing 11.10 64 bit in one partition and using the ThinkPad as my primary machine. I am a bit worried about graphics and wireless network issues, but I won't know until I install the OS. 

I hope you get your problems ironed out. I'm also interested in the OP's modifications and if anyone else has tried them out.

---

### Post by bro on 2011-11-13
I have the w520. You don't need to worry. The wifi will just work and the graphics too. Optimus won't work but you can disable it in the bios and opt for discrete or integrated. I'm doing the latter and 'no proprietary drivers are in use'. I hope optimus/bumblebee/ironhide will get working fully one day on my system though.

---

### Post by Astronaut356 on 2011-11-13
Do you have any issues with the fan in your W520? Have you installed the thinkfan package?

---

### Post by bro on 2011-11-14
Issues is not the word, it is quite quiet. I don't know if it is on all the time or not. It might be. My laptop as a whole feels cool on the outside at least. I recently heard of the thinkfan package but did not install it yet. Do you happen know any straight forward instructions for it?

---

### Post by Astronaut356 on 2011-11-14
> **bro said:**
> Issues is not the word, it is quite quiet. I don't know if it is on all the time or not. It might be. My laptop as a whole feels cool on the outside at least. I recently heard of the thinkfan package but did not install it yet. Do you happen know any straight forward instructions for it?

I'm not going to install it until I spend a little time with my T420s and see if the fan sounds like its on all the time. But here you go:


You need to create the file /etc/modprobe.d/thinkfan.conf.

I'll describe the steps in detail:

1. install thinkfan package:

$ sudo apt-get install thinkfan

2. add kernel module 'coretemp' to /etc/modules

$ sudo sh -c 'echo coretemp >> /etc/modules'

3. load kernel module 'coretemp'

$ sudo modprobe coretemp

4. add the following three sensor entries to /etc/thinkfan.conf just before the temperature levels:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.2/temp1_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

[ edit the file /etc/thinkfan.conf with your favourite editor, e.g. 'sudo gedit /etc/thinkfan.conf' ]

5. add the following to /etc/modprobe.d/thinkfan.conf: 'options thinkpad_acpi fan_control=1'

$ sudo sh -c 'echo "options thinkpad_acpi fan_control=1" >> /etc/modprobe.d/thinkfan.conf'

6. reload kernel module 'thinkpad_acpi'

$ sudo modprobe -r thinkpad_acpi
$ sudo modprobe thinkpad_acpi

7. set START="yes" in /etc/default/thinkfan

[ edit the file /etc/default/thinkfan with your favourite editor, e.g. 'sudo gedit /etc/default/thinkfan' ]

8. start thinkfan:

$ sudo /etc/init.d/thinkfan start

9. check whether it works

$ sudo cat /proc/acpi/ibm/fan

if level has a value between 0 and 7, and changes by times, your thinkfan daemon works.

---

### Post by bro on 2011-11-17
Hi, thanks, I just followed your procedure. This line: 
sensor /sys/devices/platform/coretemp.2/temp1_input 
appears not to exist:
```

@W520:~$ sudo /etc/init.d/thinkfan start
/sys/devices/platform/coretemp.2/temp1_input: No such file or directory
@W520:~$ sudo cat /proc/acpi/ibm/fan
status:		enabled
speed:		1963
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```
I removed it and re-did the procedure from there. Now:```

@W520:/sys/devices/platform$ sudo cat /proc/acpi/ibm/fan
status:		disabled
speed:		0
level:		0
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```
I'm not sure what is what however, psensor tells me:
temp1 > 37c (what's that?)
fan1 > 0
Physical id 0 > 37c (what's that?)
Core 0 > 37C
Core 1 to 3 have more or less the same (varying 34-38C). 
This is not 'hot' but how do I know what my HD temp is? 
the fan1 0 now made me a bit nervous... it used to be 2800 or so... 
(I'm going to stress my machine now and see if it turns on)

---

### Post by Astronaut356 on 2011-11-17
I followed that procedure and it didn't work for me either. I did a bit more research and found out that because of the kernel changes in 11.10, the sensor entries had to be changed to:

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input

When I made the change that did the trick. Here is what I see when I check the fan.

status:        enabled
speed:        3818
level:        3
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

---

### Post by egarim on 2011-11-19
How could you exactly known the power consumption?

---

### Post by lads on 2011-11-21
> **steevven1 said:**
> Virtually all of your power savings are coming from this kernel parameter: i915.i915_enable_rc6=1

This parameter is known to cause graphical glitches and system freezes on Sandy Bridge processors, just so you know. Are you experiencing any problems like this?

On my ThinkPad X220 (also with a Sandy Bridge i7), this kernel parameter causes HUGE power savings and also graphical glitches and freezes.

Interesting. I'm running Ubuntu on a T420 and made an early upgrade to 11.10 because of the constant system freezes. After the upgrade the battery was being drawn in under one hour. I now can make it last a bit over 2 hours by activating the fan control, but still very far from the 5 hours it would last with 11.04.

So basically you're telling us it is a matter of choice: either have a long-life battery and constant freezes or have no freezes but work with the thinkpad constantly plugged.

Btw, *add-apt-repository* doesn't seem to be available for this version of Ubuntu (yes, I already installed *python-software-properties* and still get a not found message). If someone could  post the actual lines to include in *sources.list* in order to complete junkilo's recipe it would be much appreciated.

Thanks.

---

### Post by bro on 2011-11-30
> last a bit over 2 hours by activating the fan control, but still very far from the 5 hours it would last with 11.04.
I got quite amazing results from both fan control and adding i915.i915_enable_rc6=1. My battery life went from about 4,5 hours to 5,5-6 hours on a W520.

---

### Post by lolnux on 2011-12-03
Also just installed the Ubuntu 11.10 64 bit on a t420s i7 SSD. I have use NVS 4200M graphics (set on discrete in BIOS - ubuntu works best with it on). Also tried to just use integrated -> problem still exists. So it must be with the CPU.

I have tried to install thinkfan with the configuration from this tread, but the problem is still there. [Then I found this: specific configuration for Intel Sandy Bridge CPU.]("http://www.jakubkotowski.com/2011/06/thinkpad-t420-thinkfan-settings.html") I haven't tried it yet – anybody have experience with it? Or have a thinkfan.conf file to share for a t420s i7 with SSD? (I have read that you also have to set up temp parameters for the SSD?).

On a second note, I found out that [apparently there is a fan issue with a lot of Lenovos, no matter the OS]("http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T420s-Fan-noise-Issue/td-p/443569/page/2"). I am running BIOS v. 1.29 but there is a [update v. 1.30 out]("http://support.lenovo.com/en_US/research/hints-or-tips/detail.page?LegacyDocID=MIGR-77167"). Anybody have any experience with v. 1.30?

Do anybody know if other distros, like debian, are having the same issues?

---

### Post by ultimatebuster on 2011-12-11
Just upgraded to 11.10

On 11.04, I used to have around 48C and Fans around 1900 RPM. Right now I'm hanging at around the same temperature with 3000 RPM.. Any idea what's causing that? (I'm using the identical thinkfans.conf except for the changed sensors)

```

status:		enabled
speed:		3373
level:		3
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))


```

As I recall setting up 11.04, I had to patch the source code of a driver and manually add "ThinkPad T420" in. Is this still required?

honestly the 3300 RPM is really annoying...


Also, after a watching Flash videos, the temperature stays at 63C and won't go down...
Thanks

---

