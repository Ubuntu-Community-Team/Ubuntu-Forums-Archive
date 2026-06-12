---
title: "Power Management gui"
date: 2008-11-20
forum: Hardware
---

### Post by iggykoopa on 2008-11-20
I'm working on a power management gui for wattos (a spin-off of ubuntu) and need people to start testing it out. I know a lot of people have requested something like this so hopefully this will help out. It started out in the dell section of the forums and here is the post I just made in the original thread showing how to get the gui [http://ubuntuforums.org/showpost.php?p=6217312&postcount=180](http://ubuntuforums.org/showpost.php?p=6217312&postcount=180) (don't worry I rewrote it to work on all machines not just dell's). keep an eye on the google code page as I'm working on it pretty heavily now. Just added support for ati cards today (haven't uploaded it yet, my firewall at work doesn't allow svn access) and I'll need people to test that portion out because I don't have any ati cards. Thanks to anyone that tries this out and helps getting it working good.

**New installation instructions are here [http://ubuntuforums.org/showpost.php?p=6362540&postcount=103](http://ubuntuforums.org/showpost.php?p=6362540&postcount=103)**

---

### Post by motin on 2008-11-20
I'd like to cast a vote to either:

A. (if we want to continue development in python) ...merge poweeersave's code structure (with login in one file, and all the hardware-specific commands in another - so that different files can be contributed to support different hardware configurations) and preset management, with your specific hardware commands, the tray icon and the auto-switch feature...

B (if we can do this in C...)  ...build upon kpowersave all the way, instead of writing a whole new application/GUI. kpowersave already implements a tray icon, all powerstate change detections, ability to have different savings profiles etc. 

I don't know C but can help out with python, and I like the idea of having one application solely for advanced power saving settings. On the other hand, going with B would take us furthest in means of features and interface development. What do you prefer?

PS You might want to copy/move the information on how to get the gui running from the other thread...

---

### Post by iggykoopa on 2008-11-20
here is the post from the other thread:

ok the power management gui I'm writing is coming along...as I mentioned before I'm developing it for wattos, here's the post I just made for it over there:
I've decided to go with google code for hosting the power management gui. If people could start checking out the svn version I would appreciate it. to checkout use: 
svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm 
to run it go into the wattospm directory and type: 
sudo sh -c "python powersaving.py" 
Status so far... I have the hardware autodetection done, it will automatically check if your on battery power or not and change the settings accordingly if it is in auto mode. You can change it to manual mode (for if your on a desktop or gaming) and set it to powersaving or performance. I've added in a few other power saving options, I'll document them once v .2 is done (the version your checking out). 
what's not done.... The advanced configuration gui, for now please just select basic mode. if you want to edit any settings you will have to do it manually in the config file (named conf in the wattospm directory). If you want to enable some settings that aren't turned on in basic mode go into the conf file and set detected and enabled both to = 1. The code to change the settings is all written except for usb, bluetooth, firewire, and tracker. Tracker I just haven't got to but I haven't done the other three because I'm doing testing to see if there is a way I can actually powerdown the bluetooth(I was testing it out and useing hciconfig and then rmmoding the bluetooth modules wasn't powering down the device). Anyway if you could test it out for me and put any bugs you have on the google code issues page for the project it would help out a lot. I'll be adding a few more powersaving options then start work on the advanced config gui and documentation. Shouldn't be much longer and the next version will be out(when it's ready I'll make an installer as well so all the files go in directories that make sense).


as for merging the powereesave code structure I'm takeing a look at it now I'll probably contact the author and see what he thinks but I'd prefer to stick with gtk, I probably wont do anything with kpowersave because I don't want it to be dependent on kde stuff(also I don't know c).

---

### Post by iggykoopa on 2008-11-21
ok I have the first part of the advanced mode config gui done. should be able to get the rest done tomorrow if you want to try it out. just check out from svn as shown above.

---

### Post by iggykoopa on 2008-11-23
Everything is now done on the gui except figuring out what to do for nvidia powersaving and autodetection for nvidia and ati(you can still manually select them). If you want to control the backlight with the gui you need to install xbacklight first...
sudo apt-get install xbacklight
please download and run using the instructions above, I'm considering this a RC for ver 0.2 it's pretty much feature complete but as I haven't had anybody but me really test it I'm going to wait till I see if you guys are happy with the options before I release a ver 1.0.

once I have enough people test it to be happy with it I'll make an installer and manual.

if anyone has bluetooth can they check out that option? it's still not actually powering mine down but it is removing the module so the kernel and software aren't accessing it, I just wanted to see if it's just my bluetooth or the way all of them work (I've got a dell 1420N)

---

### Post by felipefoz on 2008-11-23
> **iggykoopa said:**
> Everything is now done on the gui except figuring out what to do for nvidia powersaving and autodetection for nvidia and ati(you can still manually select them). If you want to control the backlight with the gui you need to install xbacklight first...
sudo apt-get install xbacklight
please download and run using the instructions above, I'm considering this a RC for ver 0.2 it's pretty much feature complete but as I haven't had anybody but me really test it I'm going to wait till I see if you guys are happy with the options before I release a ver 1.0.

once I have enough people test it to be happy with it I'll make an installer and manual.

if anyone has bluetooth can they check out that option? it's still not actually powering mine down but it is removing the module so the kernel and software aren't accessing it, I just wanted to see if it's just my bluetooth or the way all of them work (I've got a dell 1420N)

nice job, I think it's a good initiative, I'm going on vacation and I'm willing to help. A suggestion would be, a box, to put services to disable. But your intention is a good one, a gui where anyone can customize, because hardware will be always different and it will impossible to create something to work on all hardware
good luck

---

### Post by felipefoz on 2008-11-24
> **iggykoopa said:**
> 
if anyone has bluetooth can they check out that option? it's still not actually powering mine down but it is removing the module so the kernel and software aren't accessing it, I just wanted to see if it's just my bluetooth or the way all of them work (I've got a dell 1420N)

about the bluetooth, have you tried first to put the service down?
/etc/init.d/bluetooth stop
and then try to take down the module!

---

### Post by iggykoopa on 2008-11-24
That's what the script does now, it should do "hciconfig hci* down" as well but when I was testing it out that still didn't help(I'll probably add that in later, I just need to write the part that scans for hci devices). In powertop it says a usb device is active 100% of the time... even after I disable the usb modules too. If you have any other ideas for it I'd love the help.

---

### Post by m4cph1sto on 2008-11-25
I tried your gui last night.  The results were good - I saved about as much power (according to powertop) as I do with all the manual power tweaks I could think of, however using the gui is much easier.  A few small issues, from a user's perspective:

No AC97 power saving option.  I have an older laptop so this would be useful.

Couldn't tell if it was properly setting my wireless power savings.  I use the command "iwpriv eth1 set_power 5" to do it manually, is this the same setting you use?

After selecting "advanced mode" I couldn't figure out how to go back to "basic".  

No default settings for Nvidia.  I don't know what power saving features are available.  Manually i set powermizer to dynamic mode in my xorg.conf to reduce the clock speeds (if I set it to lowest mode the setting doesn't seem to stick).  I also use a script that turns sync to vblank off when on battery.

Today when I tried to run your gui I get an error and it doesn't start:
IOError: [Errno 2] No such file or directory: '/proc/acpi/battery/BAT0/state'

I have 2 batteries, and BAT1 and BAT2 directories, no BAT0 directory.  Don't know why this wasn't a problem yesterday, but maybe your code needs to be updated to reflect the possibilities of BAT1 and BAT2 directories.

On a side note, I think having a power saving gui is extremely important for Ubuntu.  There are two reason I would never recommend Ubuntu to a regular laptop user: (1) terrible power-saving features, and (2) major suspend/resume problems.  Ubuntu is wonderful for desktops, but awful for laptops.  I think this gui is an important step towards resolving the first of these issues, and I'm so glad that you've taken the initiative to get it done!

---

### Post by iggykoopa on 2008-11-25
thanks for the feedback. For the ac97 power saving I'll try to add that tonight. 

With wireless power saving I echo the setting to /sys/bus/pci/drivers/iwl/*card*/power_level which is for the iwl drivers... I believe the iwpriv command is for the older ipw drivers, I can try to add that in but I may have to have you put in the interface name(I might be able to figure out how to auto-detect it). 

I actually forgot to add in the part to make it go back to basic, I'll add that in too, for now you can go into the conf file and change the setting manually.

Nvidia doesn't have any options yet, gonna add the ondemandvblanks and coolbits to it, and probably have it so it'll set ondemandvblanks for compiz too. 

I'll have to modify the battery detection portion, and yes I just hardcoded BAT0 into (my bad lol). But I'm not sure how to go about checking if there are more then one battery, maybe just check the first detected battery.

I'm also going to be adding in a section to set the read ahead size for your drive, I haven't done much testing with it yet but it should allow the disk to stay spun down more if your doing anything that accesses the drive alot, like listening to mp3's.

if anyone can think of anything else that I've missed please tell me, I'm trying to make this as encompassing as I can so it will work for everybody.

---

### Post by iggykoopa on 2008-11-25
Got off early from work so heres what I just committed to svn...

ac97 added(I don't have a card needs to be tested)
ipw added, you need to go into the general tab and set what interface it is(i.e. eth1) then enable it in the gui...haven't figured out yet how to autodetect that stuff(needs testing also)
added option to switch back to basic mode
fixed the battery detection
added readahead option(basically how much of a file is buffered from the disk, the setting is in kb)

Still haven't gotten around to nvidia stuff yet, I'll do it soon just don't really feel like wrapping my head around it right now. If youll run an lspci and tell me if the line for your nvidia card says vga compatible controller maybe thats how I can autodetect it.(thats what it says on my server, if it's consistent I'll use that)

---

### Post by felipefoz on 2008-11-26
> **iggykoopa said:**
> Got off early from work so heres what I just committed to svn...

ac97 added(I don't have a card needs to be tested)
ipw added, you need to go into the general tab and set what interface it is(i.e. eth1) then enable it in the gui...haven't figured out yet how to autodetect that stuff(needs testing also)
added option to switch back to basic mode
fixed the battery detection
added readahead option(basically how much of a file is buffered from the disk, the setting is in kb)

Still haven't gotten around to nvidia stuff yet, I'll do it soon just don't really feel like wrapping my head around it right now. If youll run an lspci and tell me if the line for your nvidia card says vga compatible controller maybe thats how I can autodetect it.(thats what it says on my server, if it's consistent I'll use that)

I think you should relax on those nvidia stuffs, and we should focus on major problems, 'cause nvidia is a fixed setting, you change once, no more changes needed. A script would easily fix the problem. If you concerned just add a tab to run a script adding, the coolbits, ondemandvblankinterrupts, and the dinamic frequency options on xorg.conf. The user will have to check if the settings will work on his hardware or not.
About wireless, I use this option "iwconfig wlan0 power on" and it works very well, would it be the same thing as you're discussing?

---

### Post by iggykoopa on 2008-11-26
I can add that as an option for powering down the card, which is another good idea. But the options we are talking about there is to put it into powersaving mode, basically the card holds information and transmits it in bigger chunks so it doesn't have to transmit as often. I've got that section added just needs to be tested(for the ipw driver, I know it works for iwl). Also I have the nvidia and ati autodetection added(I feel stupid I just checked if the modules are loaded) can someone check that the ati section is working, i don't have one(the proprietary driver for ati is fglrx right?). Also figured out how to detect your username even though the program is run as root so added that.

---

### Post by iggykoopa on 2008-11-27
got the nvidia stuff working now(only applies if your using compiz) and you still need to manually set ondemandvblank in xorg.conf(I'll try to add that tomorrow). If people wanna test it up it's up on svn now.

---

### Post by felipefoz on 2008-11-27
> **iggykoopa said:**
> got the nvidia stuff working now(only applies if your using compiz) and you still need to manually set ondemandvblank in xorg.conf(I'll try to add that tomorrow). If people wanna test it up it's up on svn now.

i was trying to figure out, what does exactly do this nvidia stuff, i mean, the command line?
have you considered the suggestion, to put a place to deactivate multiple services, instead of checking, then each person could deactivate the services they want! like
services to put down - trackerd,sysklogd,smartmontools,...
could easily use the /etc/init.d/servicename stop
Just a suggestion, seeing those services keep the processor busy, not allowing to go in a deeper state.
cheers

---

### Post by iggykoopa on 2008-11-27
I can work on that, I'll probably figure out how to check which services are active and allow you to turn them off, I'll work on that in the next couple days. The nVidia stuff only applies if your using compiz, it changes sync to vblank off and changes the slide time in the wall plugin shorter so the card doesn't have to go into full power. The powermizer settings you can't change on the fly so I'll have an option to change it in xorg.conf easily, just haven't figured out exactly how I want to parse xorg.conf yet (I have some ideas though).

edit: to explain a little better it changes two keys in gconf under the compiz section.

---

### Post by felipefoz on 2008-11-29
> **iggykoopa said:**
> I can work on that, I'll probably figure out how to check which services are active and allow you to turn them off, I'll work on that in the next couple days. The nVidia stuff only applies if your using compiz, it changes sync to vblank off and changes the slide time in the wall plugin shorter so the card doesn't have to go into full power. The powermizer settings you can't change on the fly so I'll have an option to change it in xorg.conf easily, just haven't figured out exactly how I want to parse xorg.conf yet (I have some ideas though).

edit: to explain a little better it changes two keys in gconf under the compiz section.

got that part, looked into the code, and found the respective lines!
I've got more suggestions, it's up to you take it or not.

1.
#Setting ACPI Thermal Polling Frequency to 5 seconds
#Battery
echo 5 > /proc/acpi/thermal_zone/THRM/polling_frequency
#AC
echo 0 > /proc/acpi/thermal_zone/THRM/polling_frequency
Altough this value, could be higher, it stops acpi to keep pooling every second when on battery. it checks the temperature, and see if it is okay

2. Cache Writing
This option could appear by default in hdparm, i use it here
-W 1 # cache writing enabled, improves performance
-W 0 # cache writing disabled, normal performance 

3. In my case I use only wireless, and the eth0 keeps pooling, and keep processor busy
ifconfig eth0 down
mopdrobe -r forcedeth    #my ethernet module

4. Setting the highest frequency for the processor and make sure it is ondemand
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
# My processor highest is 1.9 GHZ and set it get 1.6 GHZ, it is experimental, i don't know it is worthy
echo 1600000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

5. Enable , Disable NMI_watchdog
from powertop = "The NMI watchdog is a kernel debug mechanism to detect deadlocks"
echo 0 > /proc/sys/kernel/nmi_watchdog #battery
echo 1 > /proc/sys/kernel/nmi_watchdog # AC
But it seems this option causes problem in some hardware, I think it shouldn't be enabled by default

6. Taking down gnome-power-manager
It uses to often the processor, in 8.04 I know that, I don't know about 8.10. It is better to use acpi applet to check battery state.

7. There is this program xset, which controls when the monitor is going to turn off.

I really want that program to succeed, and in the next weeks I'll be partially on vacation. And I know a hard part of doing a program, it is its documentation, which about power management, is very difficult to find. If you want, I can help you with that.
Cheers

---

### Post by iggykoopa on 2008-11-29
ok sounds good, I'll add those options when I get a chance. I appreciate the help with this.

---

### Post by iggykoopa on 2008-11-30
ok added acpi thermal polling frequency, hdparm cache writing, and nmi watchdog. Checked on gnome-power-manager and it doesn't seem to make a difference disabling it in intrepid so I'm not gonna add that unless I see a reason to. The screenshot is on my 1420N with all the relevant options on. 10 watts...not too bad. I could probably get it lower if I turned off the wifi and turned off DRI on the video card. Keep the recommendations coming on power saving options, and I'll try to get around to adding the stuff that I haven't added soon. With new ideas could everyone put them in as feature requests here [http://code.google.com/p/wattospm/issues/list](http://code.google.com/p/wattospm/issues/list) it'll just make it easier for me to track them.

edit: also heres a thread on using kernelcheck to compile your own kernel [http://ubuntuforums.org/showthread.php?t=618563&highlight=kernelcheck](http://ubuntuforums.org/showthread.php?t=618563&highlight=kernelcheck) . in case you want to enable pcie aspm. It's really easy to use, make sure you select just pcie aspm not pcie aspm debug.

---

### Post by chadeldridge on 2008-11-30
when exiting the application are settings reverted to default?

Also I am just assuming that "Enabled" actually means that in power save mode that item will be disabled.

---

### Post by iggykoopa on 2008-11-30
No the settings aren't reverted when you exit, the app is intended to be run all the time. If that feature is requested a lot though I can add it in. And your correct about the enabled, it means the setting is enabled not necessarily the service or module.

---

### Post by chadeldridge on 2008-12-01
Iggy,

Great work on this app!  For people that do not want to delve into the recesses of laptop_mode this is a great option.  I have ran both your gui and laptop_mode and currently I am almost identical on power usage between the two.  My laptop_mode config actually pulls about 1w less than using the GUI but I attribute that to the extreme amount of time and work I have put into it.  

Great work, I will continue to run tests for you as you update.  The Dell XPS M1710 runs about 39-40W normally, but with tweaking either via your gui or laptop_mode I can run around 27W .. taking a 1 hour battery to nearly 3 hours.  I am a happy camper either way.  

Thanks for your work,
Chad

---

### Post by m4cph1sto on 2008-12-01
I haven't tried your most recent update yet, but I noticed one small issue: the settings aren't applied when I resume from suspend.  For example, I need to unplug and then plug back in my AC adapter after resuming from suspend in order for the AC mode settings to be applied.  I'm not sure why this is, and I only noticed it now because I finally just got resume-from-suspend to work on my laptop :)

---

### Post by iggykoopa on 2008-12-01
I'll have to test out the resume from suspend...I actually hadn't tried that yet as I never suspend or hibernate, thanks for pointing it out.

also chadeldridge if there's anything you have set in your laptop mode config that I don't have an as option let I'd appreciate it if you let me know.

I'll probably be working on a one time option tab(if you can think of a better name tell me) which will have a xorg.conf autoconfig and powering down network interfaces next. May integrate my firefox ramdisk launcher as well but I need to do more testing to see if it's worth bothering with(need to check if it actually keeps the disk spun down more).

---

### Post by chadeldridge on 2008-12-01
When I get home I will send you all my laptop_mode config files and some other config changes that I made perminent.

---

### Post by galv on 2008-12-01
> **m4cph1sto said:**
> On a side note, I think having a power saving gui is extremely important for Ubuntu.  There are two reason I would never recommend Ubuntu to a regular laptop user: (1) terrible power-saving features, and (2) major suspend/resume problems.  Ubuntu is wonderful for desktops, but awful for laptops.  I think this gui is an important step towards resolving the first of these issues, and I'm so glad that you've taken the initiative to get it done!

What distro would you recomend for a laptop?

Thanks,
Galv

---

### Post by chadeldridge on 2008-12-01
Ready for an overkill of information?  

**laptop-mode.conf**
```
###############################################################################
#
# Configuration for Laptop Mode Tools
# -----------------------------------
#
# There is a "system" to the configuration setting names:
#    CONTROL_something=0/1   Determines whether Laptop Mode Tools controls 
#                            something
#    LM_something=value      Value of "something" when laptop mode is active
#    NOLM_something=value    Value of "something" when laptop mode is NOT
#                            active
#    AC_something=value      Value of "something" when the computer is running
#                            on AC power
#    BATT_something=value    Value of "something when the computer is running
#                            on battery power
#
# There can be combinations of LM_/NOLM_ and AC_/BATT_ prefixes, but the
# available prefixes are different for each setting. The available ones are 
# documented in the manual page, laptop-mode.conf(8). If there is no LM_/
# NOLM_ in a setting name, then the value is used independently of laptop
# mode state, and similarly, if there is no AC_/BATT_, then the value is used
# independently of power state.
#
# Some options only work on ACPI systems. They are marked ACPI-ONLY.
#
# Note that this configuration file is a fragment of shell script: you
# can use all the features of the shell scripting language to achieve your
# desired configuration.
#
# 
# Modules
# -------
#
# Laptop Mode Tools modules have separate configuration files, that can be
# found in /etc/laptop-mode/conf.d. Please look through these configuration
# files as well, there are many useful power saving tools in there!
#
###############################################################################



###############################################################################
# Configuration debugging
# -----------------------
###############################################################################


#
# Set this to 1 if you want to see a lot of information when you start/stop 
# laptop_mode.
#
VERBOSE_OUTPUT=0



###############################################################################
# When to enable laptop mode
# --------------------------
#
# "Laptop mode" is the mode in which laptop mode tools makes the computer
# consume less power. This includes the kernel "laptop_mode" feature, which
# allows your hard drives to spin down, as well as various other settings which
# can be tweaked by laptop mode tools. You can enable or disable all of these
# settings using the CONTROL_... options further down in this config file.
###############################################################################


#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0


#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0



###############################################################################
# When to enable data loss sensitive features
# -------------------------------------------
#
# When data loss sensitive features are disabled, laptop mode tools acts as if
# laptop mode were disabled, for those features only.
#
# Data loss sensitive features include:
# - laptop_mode (i.e., delayed writes)
# - hard drive write cache
#
# All of the options that follow can be set to 0 in order to prevent laptop
# mode tools from using them to stop data loss sensitive features. Use this
# when you have a battery that reports the wrong information, that confuses
# laptop mode tools.
#
# Disabling data loss sensitive features is ACPI-ONLY.
###############################################################################


#
# Disable all data loss sensitive features when the battery level (in % of the
# battery capacity) reaches this value.
#
MINIMUM_BATTERY_CHARGE_PERCENT=3


#
# Disable data loss sensitive features when the battery reports its state
# as "critical".
#
DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1


###############################################################################
# Controlled hard drives and partitions
# -------------------------------------
#
# For spinning down your hard drives, laptop mode will remount file systems and
# adjust hard drive spindown timeouts. These parameters specify which
# devices and partitions are affected by laptop mode.
###############################################################################


#
# The drives that laptop mode controls.
# Separate them by a space, e.g. HD="/dev/hda /dev/hdb". The default is a
# wildcard, which will get you all your IDE and SCSI/SATA drives.
#
HD="/dev/[hs]d[abcdefgh]"


#
# The partitions (or mount points) that laptop mode controls.
# Separate the values by spaces. Use "auto" to indicate all partitions on drives
# listed in HD. You can add things to "auto", e.g. "auto /dev/hdc3". You can
# also specify mount points, e.g. "/mnt/data".
#
PARTITIONS="auto /dev/mapper/*"


#
# If this is enabled, laptop mode tools will assume that SCSI drives are
# really SATA drives that only _look_ like SCSI drives, and will use hdparm
# to control them. Set this to 0 if you have /dev/sd devices and you want
# laptop mode tools to use the "sdparm" command to control them. 
#
ASSUME_SCSI_IS_SATA=1


###############################################################################
# Hard drive behaviour settings
# -----------------------------
#
# These settings specify how laptop mode tools will adjust the various
# parameters of your hard drives and file systems.
###############################################################################


#
# Maximum time, in seconds, of work that you are prepared to lose when your
# system crashes or power runs out. This is the maximum time that Laptop Mode
# will keep unsaved data waiting in memory before spinning up your hard drive.
#
LM_BATT_MAX_LOST_WORK_SECONDS=800
LM_AC_MAX_LOST_WORK_SECONDS=360


#
# Should laptop mode tools control readahead?
#
CONTROL_READAHEAD=1


#
# Read-ahead, in kilobytes. You can spin down the disk while playing MP3/OGG
# by setting the disk readahead to a reasonable size, e.g. 3072 (3 MB).
# Effectively, the disk will read a complete MP3 at once, and will then spin 
# down while the MP3/OGG is playing. Don't set this too high, because the 
# readahead is applied to _all_ files that are read from disk.
#
LM_READAHEAD=3072
NOLM_READAHEAD=128


#
# Should laptop mode tools add the "noatime" option to the mount options when 
# laptop mode is enabled?
#
CONTROL_NOATIME=0

# Should laptop use relatime instead of noatime? The "relatime" mount option has
# more standards-compliant semantics, and allows more applications to work,
# while retaining a low level of atime updates (i.e., disk writes).
USE_RELATIME=1


#
# Should laptop mode tools control the hard drive idle timeout settings?
#
CONTROL_HD_IDLE_TIMEOUT=1


#
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 20 seconds
# for battery and for AC with laptop mode on.
#
LM_AC_HD_IDLE_TIMEOUT_SECONDS=20
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200


#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254


#
# Should laptop mode tools control the hard drive write cache settings?
#
CONTROL_HD_WRITECACHE=1


#
# Write cache settings for HD (hdparm -W values)
#
NOLM_AC_HD_WRITECACHE=1
NOLM_BATT_HD_WRITECACHE=0
LM_HD_WRITECACHE=0




###############################################################################
# Settings you probably don't want to touch
# -----------------------------------------
#
# It is usually not necessary to change these parameters. They are included
# for completeness' sake.
###############################################################################


#
# Change mount options on partitions in PARTITIONS? You don't really want to
# disable this. If you do, then your hard drives will probably not spin down
# anymore.
#
CONTROL_MOUNT_OPTIONS=1


#
# Dirty synchronous ratio.  At this percentage of dirty pages the process
# which calls write() does its own writeback.
#
LM_DIRTY_RATIO=60
NOLM_DIRTY_RATIO=40


#
# Allowed dirty background ratio, in percent.  Once DIRTY_RATIO has been
# exceeded, the kernel will wake pdflush which will then reduce the amount
# of dirty memory to dirty_background_ratio.  Set this nice and low, so once
# some writeout has commenced, we do a lot of it.
#
LM_DIRTY_BACKGROUND_RATIO=1
NOLM_DIRTY_BACKGROUND_RATIO=10


#
# kernel default settings -- don't touch these unless you know what you're 
# doing.
#
DEF_UPDATE=5
DEF_XFS_AGE_BUFFER=15
DEF_XFS_SYNC_INTERVAL=30
DEF_XFS_BUFD_INTERVAL=1
DEF_MAX_AGE=30


#
# This must be adjusted manually to the value of HZ in the running kernel
# on 2.4, until the XFS people change their 2.4 external interfaces to work in
# centisecs. This can be automated, but it's a work in progress that still
# needs some fixes. On 2.6 kernels, XFS uses USER_HZ instead of HZ for
# external interfaces, and that is currently always set to 100. So you don't
# need to change this on 2.6.
#
XFS_HZ=100


#
# Seconds laptop mode has to to wait after the disk goes idle before doing
# a sync.
#
LM_SECONDS_BEFORE_SYNC=2
```

**ac97-powersave.conf**
```

#
# Configuration file for Laptop Mode Tools module ac97-powersave.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# AC97 power saving settings
# ---------------------------
#
# If you enable this setting, laptop mode tools will automatically set the
# powersave mode of AC97 audio chipsets. This setting does not hurt, so
# there are no AC vs. battery settings: if CONTROL_AC97_POWER is set to 1,
# the powersave mode is always enabled.
#
###############################################################################

# Control AC97 audio chipset power?
CONTROL_AC97_POWER=1

```
**bluetooth.conf**
```

#
# Configuration file for Laptop Mode Tools module bluetooth.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# Bluetooth settings
# ------------------
#
# If you enable this module, laptop mode tools will enable/disable bluetooth
# depending on the power status of your laptop. Bluetooth uses a considerable
# amount of power (comparable to wireless networking), and disabling it is
# therefore a good idea when you are looking to improve your battery life.
#
###############################################################################

# Control bluetooth?
CONTROL_BLUETOOTH=1

# Enable bluetooth on battery
BATT_ENABLE_BLUETOOTH=0

# Enable bluetooth on AC
AC_ENABLE_BLUETOOTH=1

# Bluetooth interfaces to enable/disable
BLUETOOTH_INTERFACES="hci0"


```

**configuration-file-control.conf**

```
#
# Configuration file for Laptop Mode Tools module configuration-file-control.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#

###############################################################################
# Configuration file control
# --------------------------
#
# Laptop mode tools can automatically swap out configuration files depending on
# the power state of your system.
# 
# The primary use for this feature is for controlling the configuration files
# of syslog daemons. Syslog daemons have a tendency to sync their log files when
# entries are written to them. This causes disks to spin up, which is not very
# nice when you're trying to save power. The syslog.conf can be tweaked to *not*
# sync a given file, by prepending the log file name with a dash, like this:
#
# 	mail.*		-/var/log/mail/mail.log
#
# Using the following options, you can let laptop mode switch between
# different configurations depending on whether you are working on
# battery or on AC power.
#
#
# IMPORTANT NOTE
# --------------
#
# This feature will NOT work if CONTROL_SYSLOG_CONF is set in laptop-mode.conf.
# To start using this feature, remove the CONTROL_SYSLOG_CONF section in
# laptop-mode.conf, and then restart the laptop-mode-tools service.
#
# Note that the new config files will have different names than the old ones,
# and that settings are NOT migrated. You will have to do this manually.
#
###############################################################################


#
# Should laptop mode tools control which configuration files should be used?
#
CONTROL_CONFIG_FILES=1


#
# Specify the configuration files that you want to control, as a space-separated
# list.
#
# The specific configuration files will be named as follows:
#
#     <config file>-nolm-ac
#     <config file>-lm-ac
#     <config file>-batt
#
# The first file will be used when the system is on AC power and laptop mode
# is not active. The second file will be used when the system is on AC power and
# laptop mode is active. The third file will be used when the system is on
# battery power.
#
# When the laptop mode tools service is enabled, it will replace the
# configuration files with a symlink to one of the three state-based
# configuration files. The original configuration file will be saved as
# <config file>.lmbackup, and it will be restored when the laptop mode tools
# service is disabled.
#
# When you add files to this list, make sure to also add the appropriate
# programs and services to the configuration settings below.
#
# You can create the alternate configuration files yourself. If you don't, they
# will be created by laptop mode tools the next time it is restarted. To force
# the files to be created, run the laptop mode tools init script with the
# "restart" parameter.
#
CONFIG_FILES="/etc/syslog.conf /etc/syslog-ng/syslog-ng.conf /etc/rsyslog.conf"


#
# Signal these programs and reload these services when configuration files hav
# been replaced.
#
# Programs in CONFIG_FILE_SIGNAL_PROGRAMS receive the SIGHUP signal after
# configuration files have been replaced. All common syslog daemons interpret
# this as an instruction to reload their config files, it may work for other
# daemons as well but your mileage may vary.
#
# For services listed in CONFIG_FILE_RELOAD_SERVICES, laptop mode tools will
# call the init script with the "reload" parameter after configuration files
# have been replaced.
#
CONFIG_FILE_SIGNAL_PROGRAMS="syslogd syslog-ng rsyslogd"
CONFIG_FILE_RELOAD_SERVICES=""
```

**cpufreq.conf**
```
#
# Configuration file for Laptop Mode Tools module cpufreq.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#

###############################################################################
# CPU frequency scaling and throttling
# ------------------------------------
#
# Laptop mode tools can automatically adjust your kernel CPU frequency
# settings. This includes upper and lower limits and scaling governors.
# There is also support for CPU throttling, on systems that don't support
# frequency scaling.
#
# This feature only works on 2.6 kernels.
#
#
# IMPORTANT: In versions 1.36 and earlier, these settings were included in the
# main laptop-mode.conf configuration file. If they are still present, they
# overrule the settings in this file. To fix this, simply delete the settings
# from the main config file.
#
###############################################################################


#
# Should laptop mode tools control the CPU frequency settings?
#
CONTROL_CPU_FREQUENCY=1


#
# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
# The "governor" can be any governor installed on your system, this usually
# includes "ondemand", "conservative", and "performance". The
# "IGNORE_NICE_LOAD" setting specifies that background programs that have
# a low priority ("nice level") should not cause the CPU frequency to
# be increased. (You generally want this to be enabled in battery mode.)
#
BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=ondemand
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_IGNORE_NICE_LOAD=0


#
# Should laptop mode tools control the CPU throttling? This is only useful
# on processors that don't have frequency scaling.
# (Only works when you have /proc/acpi/processor/CPU*/throttling.)
#
CONTROL_CPU_THROTTLING=0


#
# Legal values are "maximum" for the maximum (slowest) throttling level,
# "minimum" for minimum (fastest) throttling level, "medium" for a value
# somewhere in the middle (this is usually 50% for P4s), or any value listed
# in /proc/acpi/processor/CPU*/throttling. Be careful when using "maximum":
# this may be _very_ slow (in fact, with P4s it slows down the processor
# by a factor 8).
#
BATT_CPU_THROTTLING=medium
LM_AC_CPU_THROTTLING=medium
NOLM_AC_CPU_THROTTLING=minimum

```

**ethernet.conf**

```
#
# Configuration file for Laptop Mode Tools module ethernet.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# Ethernet power saving settings
# ------------------------------
#
# There are various ways to save power with ethernet. This section allows you
# to control the speed of your ethernet connection, and your wakeup-on-LAN
# settings. Both these things can have quite a power impact if you use Ethernet.
#
###############################################################################

# Control Ethernet settings?
CONTROL_ETHERNET=1

# Disable wakeup-on-LAN? This will disable wakeup-on-LAN unconditionally,
# independent of battery power. It will save power while your laptop is turned
# off or in standby mode.
DISABLE_WAKEUP_ON_LAN=1

# Limit the speed of the Ethernet connection to 100 Mbit? The difference in
# power usage between 1 Gbit and 100 Mbit Ethernet is quite large, so tuning
# can yield savings if you don't need the full speed (for instance if you only
# use Ethernet as to connect to a much slower ADSL modem).
BATT_THROTTLE_ETHERNET=1
LM_AC_THROTTLE_ETHERNET=1
NOLM_AC_THROTTLE_ETHERNET=0


# A list of the ethernet devices that should be controlled.
ETHERNET_DEVICES="eth0 eth1"
```

**hal-polling.conf**
```
#
# Configuration file for Laptop Mode Tools module hal-polling.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# HAL polling settings
# --------------------
#
# If you enable this module, laptop mode tools will control the polling of
# your CD/DVD drives by HAL. Disabling polling saves a considerable amount of
# power, but for some older CD/DVD drives it means that inserted CDs are no
# longer autodetected. In such cases, you must turn this option off.
# Alternatively, you can configure laptop mode tools to turn HAL polling on only
# when the laptop is running on AC power. This would mean that CDs are not
# autodetected while the laptop is running on battery power, but the power
# savings may be worth the extra manual labour when you insert a CD.
#
###############################################################################

# Control HAL polling?
CONTROL_HAL_POLLING=1

# Disable HAL polling on battery
BATT_DISABLE_HAL_POLLING=1

# Enable HAL polling on AC
AC_DISABLE_HAL_POLLING=0

# Drives to apply HAL polling settings to
HAL_POLLING_DEVICES="/dev/cdrom"
```

**intel-sata-powermgmt.conf**
```
#
# Configuration file for Laptop Mode Tools module intel-sata-powermgmt.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# Intel SATA power management settings
# ------------------------------------
#
# If you enable this setting, laptop mode tools will automatically enable the
# link power management mode of Intel AHCI compliant SATA chipsets.
#
###############################################################################

# Control Intel SATA chipset power management?
CONTROL_INTEL_SATA_POWER=1

```

**sched-mc-power-savings.conf**
```
#
# Configuration file for Laptop Mode Tools module sched-mc-power-savings
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# Multi-core, multi-threaded power-saving tunables for the process scheduler
# --------------------------------------------------------------------------
#
# If you enable this setting, laptop mode tools will automatically configure the
# Linux scheduler to save power on multi-core processors while running on
# battery mode.
# 
###############################################################################

# Control multi-core power-saving tunables for the process scheduler?
CONTROL_SCHED_MC_POWER_SAVINGS=1

```

**video-out.conf**

```
#
# Configuration file for Laptop Mode Tools module video-out.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# Video output control settings
# -----------------------------
#
# It is not always possible for video hardware to detect if displays are
# actually connected to VGA out and/or TV out ports. However, an enabled video
# output port draws power, even if no display is connected. This module allows
# you to force display outputs off depending on the power mode.
#
###############################################################################

# Control video output settings?
CONTROL_VIDEO_OUTPUTS=1

# Display types to disable in various modes. Run "xrandr" to check which outputs
# are available. Make sure that you do not list your primary display here!
BATT_DISABLE_VIDEO_OUTPUTS="TMDS VGA"
LM_AC_DISABLE_VIDEO_OUTPUTS="TMDS VGA"
NOLM_AC_DISABLE_VIDEO_OUTPUTS=""
```

**wireless-iwl-power.conf**
```
#
# Configuration file for Laptop Mode Tools module wireless-iwl-power.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# IWL Wireless Power settings
# ---------------------------
#
# If you enable this setting, laptop mode tools will automatically set the
# powersave mode of Intel 3945 and 4965 wireless adapters when using the
# iwl3945 or iwl4965 drivers.
#
###############################################################################

# Control Intel IWL wireless power?
CONTROL_IWL_POWER=1

# Levels passed to "/sys/class/net/*/device/power_level" for the iwlwifi
# wireless chipsets. The allowed values are:
# 1 = fixed values with most power usage
# ...
# 5 = fixed values with least power usage
# 6 = AC (full power)
# 7 = Battery (least power)
IWL_AC_POWER=6
IWL_BATT_POWER=7

```

---

### Post by chadeldridge on 2008-12-01
Here is powertop with and without your application running and with no power management.

---

### Post by chadeldridge on 2008-12-01
Also I do not think the power management for wifi does anything at all on my laptop, either via laptop_mode or the GUI.  This is probably due to using the iwlagn driver.  Could you possibly add it to your GUI?

---

### Post by felipefoz on 2008-12-01
> **chadeldridge said:**
> Also I do not think the power management for wifi does anything at all on my laptop, either via laptop_mode or the GUI.  This is probably due to using the iwlagn driver.  Could you possibly add it to your GUI?

My wlan driver doesn't have any power management, I use the ath5k driver
and the only power management I can get it's the "iwconfig wlan0 power on" which decreased a lot the power usage from wireless
I tested theg last version of the GUI, and I could drop from ~ 22W in AC, for 12.8 W with the power management options, great job.

---

### Post by iggykoopa on 2008-12-01
I'll take a look at the configs you sent at work tomorrow, playing scatagories with the wife tonight.

The iwlagn driver should be covered by the intel iwl wireless section in the network tab, if you look at the config file in the iwl_wifi section if the dirs option has anything after it, it should be working. If not let me know, the autodetection may not be working right.

I'll look into the iwconfig power on stuff and see what drivers that'll apply to.

---

### Post by chadeldridge on 2008-12-02
Yeah,  sorry for the overkill, but i figured if you missed anything at all it would be in those files.  My wireless is what kills me using up a lot of power on its own.  Turning it off makes my battery go to around 3.6 hours, but what good is a laptop with no internet.  I do remember something from windows reguarding the eth0 card that they disabled it on battery because its polling for a connection sucked a lot of juice.  I am not sure if the same would apply for linux or not though.  I think the stack in linux does not get built until a connection is made, but again, not totally sure.

---

### Post by iggykoopa on 2008-12-02
No it wasn't overkill, I appreciate it. It looks like the only stuff I haven't added already are some ethernet stuff(turn off WOL and throttle it), on the bluetooth section I just remove the modules need to set it up so hciconfig powers down the device first, and I don't have it change the logging to log files. I'll look into adding that stuff and see if it helps more.

---

### Post by chadeldridge on 2008-12-02
That may be what is causing the very slight difference between my laptop_mode and your GUI .. its a very slight .4-.7W.

On an edited note .. with hard use on battery i get 1hour 48 minutes on laptop_mode and 1hour 40 minutes using he GUI .. so it is very slim difference.

---

### Post by chadeldridge on 2008-12-02
Mind also taking a look at the sata power management stuff.  I am getting an error when i turn on the link management power management in the GUI:

```
sh: cannot create /sys/class/scsi_host/host0/link_power_management_policy: Directory nonexistent
sh: cannot create /sys/class/scsi_host/host1/link_power_management_policy: Directory nonexistent


```

I am also getting a crazy amount of HDD spin up and down .. about every 10 seconds... any ideas?

---

### Post by iggykoopa on 2008-12-02
hmmm that's weird...in the autodetection for the sata hosts it checks if those directories exist, if you don't mind try resetting your settings(on the general tab) and see if it still does it. For the disks spinning up could you install iostat and see what apps are causing the disk to spin up for you? it may be the logs because I haven't done that section yet, or possibly if your using firefox(I've got a script that loads the firefox cache into ramdisk, still need to integrate it though).

edit: did some more looking into it, and my laptop was actually doing the same thing, I increased the power saving settings for dirty ratio, dirty writeback, and journal commit to a lot higher (added a 0 to the end of each of them) and got the disk to stay spun down for about 30 seconds at a time. Monitored with iotop but I couldn't see anything else accessing the drive so I'll have to do more testing. If increasing those settings helps you as well I may do that for the defaults, just have to add a big warning that if you enable those and lose power you can lose data.

another edit: did some testing with the firefox script while I was at it, and it doesn't really help. Firefox is just horrible about writing to the disk, I'll try modifying the script to copy the whole .firefox directory to ramdisk if you have enough ram if that'll help and I'll try testing some alternate browsers like dillo2 and midori to compare.

---

### Post by iggykoopa on 2008-12-02
Ok I was starting the section on the logs and noticed mine was already set correctly and I had never changed it. If some people don't mind running the attached script and telling me the results I would appreciate it. If the results look like:
eric@lappy:~/Desktop$ python log.py 
	mail,news.none		-/var/log/messages
then I don't need to add that section because it's the default already. If it looks like:
eric@lappy:~/Desktop$ python log.py 
	mail,news.none		/var/log/messages
then I will have to do it.
If you don't want to run the script you can just open /etc/syslog.conf and look for the line like that manually, just wanted to make it easier for you guys(and girls).

---

### Post by iggykoopa on 2008-12-03
Ok did some more testing and the two biggest things causing writes to disk were gconf(don't know what to do to fix that) and for some reason winbindd, so I'll probably add an option in the services section to turn off winbind since you don't need it unless your using samba. If anyone else wants to do some more testing and see what programs and services are bad about writing to disk use iotop and:

- If you find the disk spinning up too often, try(stolen from vor's post about powersaving):

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog
```

Then, to turn that functionality off:

```
sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
```

also like I said before if your trying to keep the disk spundown never use firefox, I'll be testing out the alternatives to see what's the best for disk-writes.

---

### Post by loomsen on 2008-12-03
Humm, looking nice, good job I think ^^ Actually I'd probably fancy using it, tho, actually, I'm looking for one option only.

Is it possible to set up a custom load value for the bat?

This would be the most important option for me. I think I've been reading any file in my /proc and /sys at least twice, but none had an apropriate option.

I'm usually on AC most of the time. Maybe once every 2 months or so I need the portable attributes of my laptop.
Thus, having my battery load at 35-40% rather than 100% would help me a lot.
So, is this possible anyhow?

---

### Post by iggykoopa on 2008-12-03
by load do you mean recharge to 30-40% ? If so I've never seen an option to do that. Most of what I've seen people recommend though is to recharge the battery to 100% then physically remove it until you need it(some laptops act funny when you remove the battery though). If that is what you meant I can look into it some more and see if it's an option.

---

### Post by chadeldridge on 2008-12-03
> **iggykoopa said:**
> Ok I was starting the section on the logs and noticed mine was already set correctly and I had never changed it. If some people don't mind running the attached script and telling me the results I would appreciate it. If the results look like:
eric@lappy:~/Desktop$ python log.py 
	mail,news.none		-/var/log/messages
then I don't need to add that section because it's the default already. If it looks like:
eric@lappy:~/Desktop$ python log.py 
	mail,news.none		/var/log/messages
then I will have to do it.
If you don't want to run the script you can just open /etc/syslog.conf and look for the line like that manually, just wanted to make it easier for you guys(and girls).

I will get you all this tonight from my laptop, i really should have brought it to work today.

---

### Post by iggykoopa on 2008-12-03
ok so I did some more browser testing, midori writes almost as bad as firefox and kazehakesa wasn't usable(kept segfaulting). But dillo2 was quit useable for general browsing(no flash or cookies) and it hardly ever wrote to disk. So my recommendation for laptop browsing is dillo2, it's not in the repos yet but if you go here [http://misc.andi.de1.cc/dillo/](http://misc.andi.de1.cc/dillo/) you can use the debian lenny deb. I'm also going to look into if the script runs on a distro like slitaz that loads entirely to ram to see what kind of powersaving you can get by not using the disk at all.

---

### Post by chadeldridge on 2008-12-03
Through all this i have negected to mention that i am using reiser and not ext3 ... i think all the HDD settings for cache and writeback only effect ext3.  Can you confirm that?  If so I will be going back to it.

---

### Post by iggykoopa on 2008-12-03
I'm using reiser as well(hate the filesystem checks on ext3) and they work for reiser. The dirty writeback and similar settings are not filesystem dependent, only thing that is filesystem dependent is journal commit and that does work on reiser.

---

### Post by chadeldridge on 2008-12-03
ok great then .. i always hated that about ext3 .. plus reiser is just so much faster for moving large amounts of data around.

---

### Post by chadeldridge on 2008-12-03
Btw:
python log.py 
	mail,news.none		-/var/log/messages

---

### Post by felipefoz on 2008-12-03
@iggykoopa

python log.py
	mail,news.none		-/var/log/messages

you wrote wrong the acpi thermal polling code, it is THRM, instead of THM! =)
Ah thanks for the kernel tip, i dropped more .7 W with pcie_aspm module. Although I need to use pcie_aspm=force in kernel line.
Just a suggestion, but is there anyway to, instead of using that checkbox to say if it is detected or not, turn the checkbox inactive and the whole line becomes gray, non active and non editable?

---

### Post by chadeldridge on 2008-12-03
I might be totally off base but the settings for Dirty_background_ratio is a % from 0 -100 that tells the system how much memory it will fill before it writes the cache to disk .. in your setup you have 1 for power saving and 5 for performance.. wouldnt the exact oposite apply if you wished to keep the hdd as much as possible?

---

### Post by iggykoopa on 2008-12-03
dirty ratio is what your thinking of for the percentage, I'll have to look into what the dirty background ratio is but the settings I have are what everyone else is using in their scripts. Also with the battery thermal management it's thm on my laptop, I thought you made the typo :( I guess I'll have to make it detect which is ok for your laptop then. thanks for pointing it out. The reason I didn't want to grey out a line if it isn't detected is incase any of my autodetection code didn't function correctly people could still override it easily. But if people would prefer it that way it wouldn't be too hard to change it. You would still be able to override the autodetection manually in the config file.

---

### Post by iggykoopa on 2008-12-04
ok I've done some more testing and it seems like the script in it's current form is about as low as I'm going to be able to get on my machine, I'll still need to add the stuff on the last couple pages and any other stuff for other hardware. Anyway I've tested openbox instead of gnome, ext2 so theres no journal and a couple other things...it seems the lowest power usage I can eek out of a 1420 is about 9.8 watts, not bad but I was hoping I could do better. So now that I'm done with my testing for the moment I'll get back to coding, sorry for the delay on implementing the stuff on the last couple pages, just wanted to make sure there weren't any other recommendations I could make on configurations outside of the scope of the script. Also it doesn't seem like the effort of getting an os to run from ram is really worth it, seems like the powersaving you'll get from it is pretty minimal compared to the effort it takes. I may do a little more testing in that area once I'm caught up on the bugs you guys have given me so far though. again thanks for the help testing this, couldn't do it without you.

---

### Post by felipefoz on 2008-12-04
> **iggykoopa said:**
> dirty ratio is what your thinking of for the percentage, I'll have to look into what the dirty background ratio is but the settings I have are what everyone else is using in their scripts. Also with the battery thermal management it's thm on my laptop, I thought you made the typo :( I guess I'll have to make it detect which is ok for your laptop then. thanks for pointing it out. The reason I didn't want to grey out a line if it isn't detected is incase any of my autodetection code didn't function correctly people could still override it easily. But if people would prefer it that way it wouldn't be too hard to change it. You would still be able to override the autodetection manually in the config file.

Ow, that's true. I've been reading here, and the name of the thermal_zone is different, according the BIOS vendor. What I know is that there is only one folder inside, this thermal_zone folder, so you could use something like a * (i don't know python), instead of THM, or THRM, TZ1, etc.

---

### Post by iggykoopa on 2008-12-04
ok if there is only one folder in it then that should be easy. (in python I would use os.listdir to find the names of the folders) Thanks

---

### Post by iggykoopa on 2008-12-04
ok I fixed the thermal management portion if you want to test it out. I also set it to disable laptop mode when it starts, found out that was what kept spinning the disks back up, try testing it out and see if it works better. I don't have it turn laptop mode back on after so if you want to re-enable it do:
sudo /etc/init.d/laptop-mode start

edit: also changed the bluetooth section to use hciconfig, only issue with this is your bluetooth needs to be on during the autodetection portion.

---

### Post by chadeldridge on 2008-12-05
I get errors:

```
* Disabling laptop mode...                                                                 [ OK ] 

/dev/sda:
 setting Advanced Power Management level to 0x01 (1)
 setting acoustic management to 128
 setting drive write-caching to 0 (off)
 setting standby to 4 (20 seconds)
 write-caching =  0 (off)
 acoustic      = 128 (128=quiet ... 254=fast)
Polling is already disabled on the given drive.
ERROR: Module sbp2 does not exist in /proc/modules
ERROR: Module ohci1394 does not exist in /proc/modules
ERROR: Module ieee1394 does not exist in /proc/modules
Traceback (most recent call last):
  File "powersaving.py", line 964, in <module>
    Initialize()
  File "powersaving.py", line 24, in Initialize
    AutoSet()
  File "powersaving.py", line 951, in AutoSet
    change_power_mode("saving")
  File "powersaving.py", line 922, in change_power_mode
    for zone in Config.get("acpi_therm", "dirs").split(","):
  File "/usr/lib/python2.5/ConfigParser.py", line 520, in get
    raise NoOptionError(option, section)
ConfigParser.NoOptionError: No option 'dirs' in section: 'acpi_therm'
chad@laptop:~/power/wattospm$ 


```

Nevermind .. overwrote the cconfig file with defaults and its starting now.

---

### Post by felipefoz on 2008-12-05
> **iggykoopa said:**
> ok I fixed the thermal management portion if you want to test it out. I also set it to disable laptop mode when it starts, found out that was what kept spinning the disks back up, try testing it out and see if it works better. I don't have it turn laptop mode back on after so if you want to re-enable it do:
sudo /etc/init.d/laptop-mode start

edit: also changed the bluetooth section to use hciconfig, only issue with this is your bluetooth needs to be on during the autodetection portion.

Just a question, it may seem dumm, but...
What does exactly do this laptop-mode? Power management?
Isn't that exactly what this GUI is doing? 
If yes, what's the point of keeping laptop-mode on or even an option to turn it on?
As you said now, you are turning it off before starting the program, right?
Let's just consider then, laptop-mode and wattospm do the same thing?

---

### Post by iggykoopa on 2008-12-05
I'll probably be removing the laptop mode option soon. Yes it does do the same thing as the gui, but I had it is an option before in case someone had stuff configured there that I hadn't added to the gui yet. The gui has almost every option that someone would put in there, except the stuff in the last couple posts that I haven't made yet, so I'll be removing the option to use it because it can override some of the settings from the gui.

---

### Post by felipefoz on 2008-12-05
> **iggykoopa said:**
> I'll probably be removing the laptop mode option soon. Yes it does do the same thing as the gui, but I had it is an option before in case someone had stuff configured there that I hadn't added to the gui yet. The gui has almost every option that someone would put in there, except the stuff in the last couple posts that I haven't made yet, so I'll be removing the option to use it because it can override some of the settings from the gui.

ok, now i got it.
Another suggestion, i was just searching things about python in internet, and i found something about python-notify, the famous gnome balloons, it seemed not so difficult to use it. There are a couple examples in /usr/share/doc/ptyhon-notify/examples/* . Have a look there, when you have available time? ;)

---

### Post by iggykoopa on 2008-12-05
took a look around the web and it looked pretty easy to add some notifications. Besides notify of mode change is there anything else you think it should notify of?

---

### Post by felipefoz on 2008-12-05
> **iggykoopa said:**
> took a look around the web and it looked pretty easy to add some notifications. Besides notify of mode change is there anything else you think it should notify of?

not really, nothing comes to my mind at the moment.
Waiting for further svn updates! 
see ya

---

### Post by chadeldridge on 2008-12-05
Agreed .. remove laptop_mode and im good to go as well .. I am already removing the laptop_mode packages and killing my custom stuff, I would much rather use the GUI any day.

---

### Post by iggykoopa on 2008-12-06
New version in svn, now has notifications and I removed the laptop mode stuff. It still just disables laptop mode when it starts, if you want I can have it re-enable it when it's closed, but I figured if people where using this for power management they don't really need laptop mode anymore.

---

### Post by chadeldridge on 2008-12-06
A couple of questions:

1.  General Tab:  Interface:  This is not autofilling on my machine, is this looking for eth0 or wlan0?  

2.  Disks:  Sata Hosts:  Also not autofilling with any data, although both host0 and host1 exist in mydirectory.  Manually specifing them produces errors though due to the non existent power_management directory.

---

### Post by iggykoopa on 2008-12-06
interface has to be set manually...it is only if your using the ipw driver though, if not you can leave it blank. Sata hosts should be left blank if you don't have the power management directory, if you don't have that directory they can't be managed(in the auto-detection it checks for the directory, thats why your hosts don't show up). I'll start working on documentation soon, the program has enough options now it can be confusing with docs.

---

### Post by iggykoopa on 2008-12-07
added an installer now and changed some of the file names. You have to install for it to run now. to download the svn version run this in a terminal:
```

svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm 
cd wattospm
sudo python installer.py install
```

then to run the program:
```

sudo wattospm.py

```

you can now add it to your startup programs under sessions as:
gksudo wattospm.py

when you start up it will ask for your root password, I'll try to find a way to have it startup automatically without needing your password. If you want to uninstall type(from the svn directory):
```

sudo python installer.py uninstall

```

When a new version comes out in svn just run the installer again, it'll remove the old version and install the new(it'll also remove your config but it's easy to set back up).

edit:
there is now a little extra to the program...it has been split into a daemon and gui...the new information is here [http://ubuntuforums.org/showpost.php?p=6353702&postcount=91](http://ubuntuforums.org/showpost.php?p=6353702&postcount=91) use the instructions from here up till the installation, then follow the rest in the thread referenced.

---

### Post by loomsen on 2008-12-07
> **iggykoopa said:**
> by load do you mean recharge to 30-40% ? If so I've never seen an option to do that. Most of what I've seen people recommend though is to recharge the battery to 100% then physically remove it until you need it(some laptops act funny when you remove the battery though). If that is what you meant I can look into it some more and see if it's an option.

Well, actually, to store the load should be between 30% and 40%, regarding maximum lifetime and capacity preserving.(Storing in a fridge would be of advance too, regarding my notebooks manual.)

What I mean is, I'd like to leave my battery in my laptop all the time, but instead of being charged to 100% when I'm on AC, I'd like to have it charged to 35% only. Just limit the charge rate.
That would help preserving maximum capacity of the battery, which usually decreases in time. (Infos about load capacities mentioned from my notebooks manual)

That's my actual proc info:

```

[color=red]docter[/proc/acpi/battery/BAT1][/color] cat info 
present:                 yes
design capacity:         4800 mAh
last full capacity:      4800 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3465U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                COMPAL  
[color=red]docter[/proc/acpi/battery/BAT1][/color] cat state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      4800 mAh
present voltage:         11100 mV
[color=red]docter[/proc/acpi/battery/BAT1][/color] 

```

Thanks for your effort, appreciate it a lot.

---

### Post by iggykoopa on 2008-12-07
I'll look into it but I don't think it's going to be something I can do with this. If you find an app or code that allows you to do that let me know and I can try to integrate it.

---

### Post by loomsen on 2008-12-08
Alright, I will. Thanks for your effort anyway :)

---

### Post by felipefoz on 2008-12-08
> **iggykoopa said:**
> added an installer now and changed some of the file names. You have to install for it to run now. to download the svn version run this in a terminal:
```

svn checkout [http://wattospm.googlecode.com/svn/trunk/](http://wattospm.googlecode.com/svn/trunk/) wattospm 
cd wattospm
sudo python installer.py install
```

then to run the program:
```

sudo wattospm.py

```

you can now add it to your startup programs under sessions as:
gksudo wattospm.py

when you start up it will ask for your root password, I'll try to find a way to have it startup automatically without needing your password. If you want to uninstall type(from the svn directory):
```

sudo python installer.py uninstall

```

When a new version comes out in svn just run the installer again, it'll remove the old version and install the new(it'll also remove your config but it's easy to set back up).

The installation worked fine, and now I'm running the program as default program. hehehe
One thing I've just figured out today, is that xbacklight doesn't work by me, and I saw related issues to another users, is there another program for similar use? 
when I had my power savingscript I used the
echo 20 > /proc/acpi/video/Z004/LCD0/brightness
But this is very different for each laptop


Another suggestion, to become more user friendly, the filling boxes, some of them could be replaced by those with arrows, where you click the arrow and in(de)creases number, and in a middle column put the units, KB, or Seconds, or anything like. Those with two options only, just replace with an on or off button. As I said, just suggestions
edit:
By the way, just reading some docs, I saw this options swappiness, I thought it'd be interesting putting it on, since some people have less physical memory, for they it would make a difference in how it is used the virtual memory

---

### Post by felipefoz on 2008-12-08
@iggykoopa
I am sending a doc file, I don't know if it what you looking for, but it is a beginning. I gathered some information in the Internet, along manual pages, and kernel documentations. Sorry for the misspellings words, English is not my native language.
After this you can think about launching a debian package.
a preview, not finished yet.

---

### Post by loomsen on 2008-12-08
You may use 
/etc/laptop-mode/conf.d/lcd-brightness.conf
if you're using laptop mode anyway.
But note that you have to specify which interface to use to alter brightness, so you're basically still using the same interface. This interface, however, should be located under
/proc/acpi/video/*
for most laptops. From there the name probably will defer, but basically, for altering brightness, 
/proc/acpi/video/
is the directory to take a closer look at.

xbacklight, however, doesn't use acpi but the xrandr extension.

For usage hints and further information try the common tools, like man, whatis and apropos:
```

man xrandr
whatis xrandr
apropos xrandr

```

apropos and whatis are nice tools to get a basic idea of what an app does/is. It shows different related tools/applications, usually followed by a number in brackets. This shows which manual is available. 
So, for instance, this is what it shows here:
> 
[color=red]docter[/proc/acpi/video/GFX0/DD02][/color] apropos xrandr
Xrandr (3)           - X Resize, Rotate and Reflection extension.
xrandr (1)           - primitive command line interface to RandR extension
[color=red]docter[/proc/acpi/video/GFX0/DD02] [/color]


So that these commands should show manuals for xrandr:
[b]man 1  xrandr
man 3 Xrandr[/b]

For general manual usage information, you may run
**man man**

---

### Post by iggykoopa on 2008-12-08
Thank you for the on the documentation, it is a good start. If you want to continue with it I would appreciate it. With the lcd brightness I can work on something using /proc/acpi/video/ but it will take me a little bit to figure it out. If you guys think of anything else or find any more bugs let me know, chadeldridge found a bug in the nvidia settings I'm trying to figure that one out now.

---

### Post by iggykoopa on 2008-12-09
added autodetection for network interfaces and now you have a dropdown for ipw wireless. I put this in place so next I can add a one-time options tab and you'll be able to set interfaces up and down from a drop-down box.

---

### Post by cheaptrick on 2008-12-09
i got this when i ran in the terminal sudo wattospm.py

Traceback (most recent call last):
  File "/bin/wattospm.py", line 971, in <module>
    Initialize()
  File "/bin/wattospm.py", line 11, in Initialize
    Config.readfp(ConfigFile)
  File "/usr/lib/python2.5/ConfigParser.py", line 286, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.5/ConfigParser.py", line 462, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /etc/wattospm/config, line: 1
'<<<<<<< .mine\n'

---

### Post by felipefoz on 2008-12-09
So, I've been researching here, and I found out it is very difficult to detect laptop brighthess, mainly because it is very, but very different for each laptop vendor. I was trying to figure out how gnome-power-manager does it, as it easily manages almost every laptop brightness, and it uses something with gconf, and xrandr, that's what I understood in the code, I don't really know C.

---

### Post by iggykoopa on 2008-12-09
cheaptrick it sounds like your config file is blank for some reason. If you type in:
```

cat /etc/wattospm/config

```
does it say anything?

felipefoz xbacklight that I'm using now also uses xrandr so I'll stick with that...maybe I'll put in a place for someone to manually put in their options and directory for /proc/acpi/video.

---

### Post by felipefoz on 2008-12-09
okay, that would seem more reasonable to me, instead of programming lines and more lines to detect it! It's easier to show people how to find the folders, as laptop-mode does.

---

### Post by motin on 2008-12-09
To prevent having to enter root password upon startup - and to make it all a bit more safe - the code should be divided into a deamon part (with the power state detection and state change code, and an application/applet that reads the status of the deamon (in order to display the right icon color), and has a menu entry to Change settings (here gksudo can be used to launch the settings pane). Upon apply settings, the deamon should be restarted.

---

### Post by iggykoopa on 2008-12-09
I was thinking about doing it that way before, but since I'm just learning python I wanted to get it working in the first place. Now that its working ok I may seperate the portions, it would make things a lot easier. If I get time I can start working on it tonight.

Edit: also if anyone is familiar with python and dbus could you help me out with the bug here [http://ubuntuforums.org/showthread.php?t=1005160](http://ubuntuforums.org/showthread.php?t=1005160) ?

---

### Post by iggykoopa on 2008-12-09
Ok I think I have it daemonized now but I'll have to wait till I get home to test the code. I'll be implementing a log for it soon since now you won't be able to see the output from the commands. I did have one question though, how should I set the permissions on the config file? the deamon reads the settings from config and the user writes to the config to change the options, that way the gui doesn't need to be run as root, but to write to the config either it needs to be owned by the user or writeable by everyone. I don't want it to be writeable by everyone because that would be a security risk, but I want the program eventually to be multi-user. Should I have the installer create a new group that has permissions on that file and add the user to it? The group could be wattospowermanagers or something like that.

edit: I didn't want to use gksudo to edit the config because it would be annoying to have to type in the root password every time you wanted to change the config, if people think it would be more secure that way I could do it though.

---

### Post by felipefoz on 2008-12-09
> **iggykoopa said:**
> Ok I think I have it daemonized now but I'll have to wait till I get home to test the code. I'll be implementing a log for it soon since now you won't be able to see the output from the commands. I did have one question though, how should I set the permissions on the config file? the deamon reads the settings from config and the user writes to the config to change the options, that way the gui doesn't need to be run as root, but to write to the config either it needs to be owned by the user or writeable by everyone. I don't want it to be writeable by everyone because that would be a security risk, but I want the program eventually to be multi-user. Should I have the installer create a new group that has permissions on that file and add the user to it? The group could be wattospowermanagers or something like that.

edit: I didn't want to use gksudo to edit the config because it would be annoying to have to type in the root password every time you wanted to change the config, if people think it would be more secure that way I could do it though.

You can do just like another gnome apps, where there is a button to "unlock" to edit the preferences, It is a good option (and safe), because these settings we are not going to change all the time.

---

### Post by cheaptrick on 2008-12-09
typed cat /etc/wattospm/config
got this

<<<<<<< .mine
[iwl_wifi]
dirs = iwlagn/0000:03:00.0
saving_setting = 5
performance_setting = 6
enabled = True
detected = True
=======
[config]
first_run = True
mode = 
root_drive =
root_partition = 
cdrom =
activation =
smp = False
username =
interfaces =
notifications = True
>>>>>>> .r29

[dirty_background_ratio]
performance_setting = 5
detected = True
enabled = False
saving_setting = 1

[dirty_writeback]
performance_setting = 90
detected = True
enabled = False
saving_setting = 60000

[bluetooth]
detected = False
enabled = False
modules = rfcomm,bnep,sco,l2cap,uhci_hcd, btusb,bluetooth
devices = sh

[readahead]
performance_setting = 256
detected = True
enabled = False
saving_setting = 1280

[dirty_ratio]
performance_setting = 10
detected = True
enabled = False
saving_setting = 90

[usb]
detected = True
enabled = False
modules = usbhid,uhci_hcd,ehci_hcd

[firewire]
detected = False
enabled = False
modules = sbp2,ohci1394,ieee1394

[intel_sound]
performance_setting = 0
detected = True
enabled = True
saving_setting = 10

[sata]
saving_setting = min_power
performance_setting = max_performance
enabled = True
detected = False
hosts = 

[tracker]
detected = True
enabled = False

[journal_commit]
performance_setting = 60
detected = True
enabled = False
saving_setting = 600

[config]
username = junhong
first_run = False
root_drive = /dev/sda
activation = auto
smp = True
cdrom = /dev/scd0
mode = advanced
interface = 
root_partition = /dev/sda8
notifications = True

[acpi_therm]
dirs = THRM
saving_setting = 0
performance_setting = 2
enabled = True
detected = True

[sched_mc]
performance_setting = 0
detected = True
enabled = True
saving_setting = 1

[window_manager]
performance_setting = compiz
detected = True
enabled = False
saving_setting = metacity

[ac97_sound]
performance_setting = 0
detected = False
enabled = True
saving_setting = 1

[hdparm]
performance_setting = -B 200 -S 240 -M 254 -W 1
detected = True
enabled = True
saving_setting = -B 1 -S 4 -M 128 -W 0

[xbacklight]
performance_setting = 100
detected = False
enabled = False
saving_setting = 50

[ipw_wifi]
performance_setting = 6
detected = False
enabled = False
saving_setting = 5
interface =

[webcam]
detected = False
enabled = False
modules = uvcvideo

[pcie_aspm]
performance_setting = default
detected = False
enabled = False
saving_setting = powersave

[ati]
performance_setting = 2
detected = False
enabled = False
saving_setting = 1

[nmi_watchdog]
performance_setting = 1
detected = True
enabled = False
saving_setting = 0

[nvidia]
performance_setting = 1,.3
detected = True
enabled = False
saving_setting = 0,.1

[hal_polling]
detected = True
enabled = False

---

### Post by iggykoopa on 2008-12-10
Ok your config file is correct, I'm working on some changes now. Once I get done with this you can try the new version and see if that fixes it. Hopefully I'll be done in a day or two.

edit: also I will probably go with making a group for permissions to the config file for now, I will go to the "unlock" button eventually. The unlock button is policykit which from looking it up seems a little complicated, I'm having enough trouble daemonizing the app now without extra confusion :P

---

### Post by chadeldridge on 2008-12-10
Cheaptrick:  I had the same issue actually, just uninstall and install it again and re-setup your values.  Worked for me.

---

### Post by cheaptrick on 2008-12-10
yes i've tried uninstalling and installing, still did not work for me

---

### Post by chadeldridge on 2008-12-10
I also removed my config file and replaced it with the config.default file:

rm config 
cp config.default config

Try that and then do the uninstall 
sudo python installer.py uninstall
sudo python installer.py install

---

### Post by iggykoopa on 2008-12-10
you shouldn't have to do all that, the installer removes the old files and copies the new when you install. I did find a bug in it that may be causing your problem but it'll be another day or two before I post the new version, went snowboarding today so I'm exhausted.

---

### Post by chadeldridge on 2008-12-11
I realize you probably shouldnt have to, but i counldnt find any other way to make it work.  Anyway, that is what i did to get it working again.  Thanks for your hard work on this Iggy.

---

### Post by iggykoopa on 2008-12-11
no problem, I'm enjoying writing this. It's a good way to learn python, and I appreciate the help you guys are giving in getting all the bugs ironned out and giving me new stuff to work on :D .

---

### Post by chadeldridge on 2008-12-11
The drive spin up and down is really starting to worry me .. its pretty much constantly parking and spinning back up.  I think for the time being I am going to disable the disk features until I am sure this is safe.

---

### Post by iggykoopa on 2008-12-11
ok that sounds fine, all you have to do is set the -B setting in powersaving mode to 254 and it will keep your drive spun up all the time. Are you using firefox while it's doing this? It's a known bug in firefox that it keeps the disks spun up, if thats the problem you can either use dillo2 when your off battery or you can try the firefox launcher I'm attaching. It loads your firefox into a ramdisk and backs it up using rsync every ten minutes(make sure you have rsync installed first) the only problem so far with the script is make sure you shut down firefox before you shut the computer down(it'll restore from the backup on the next launch but you may lose a couple minutes of work). Also if your concerned about the load cycle count here [http://ubuntuforums.org/showthread.php?t=805570&highlight=load+cycle+count](http://ubuntuforums.org/showthread.php?t=805570&highlight=load+cycle+count) is a guide on how to check it.

edit: I'm not sure how yours will be but I've had my laptop for about a year and my load cycle count is around 82,000 on the guide it says most drives last around 600,000 so I'm not too concerned on mine.

edit again: make sure before you run the script that you have enough free memory, run:
```

du -sh ~/.mozilla/firefox
free -m

```
and make sure the first number is not bigger than the amount free reported by free -m.

---

### Post by iggykoopa on 2008-12-12
ok seperated it into a daemon and gui now. New version is in svn, but I need help writing the init script for the daemon, if no one around here knows how to write one then I'll do some more research and figure it out.
To run the daemon for now until the init script is done use(when you run it you don't get any output....it's a daemon):
```

sudo wattospm-daemon.py

```
it will log to /var/log/wattospm/log, if the log starts getting too big you can go in the config file at /etc/wattospm/config and set log to False. I'll add an option for that in the gui soon. now you can run the gui as a regular user.
```

wattospm.py

```
I'll try to do some more research on policy-kit and see if I can use that in the future. Now it creates a group called powermanagers and adds the user that installed wattospm to it, if you want other users to be able to control the gui you will have to add them to that group. After you install you will have to log out then back in so the permissions for that group will work correctly. Once the init script is done you wont have to start the daemon manually each time. (hopefully this also fixed the bug with the config file, it wasn't saving the config to the right place in one line of the code)

---

### Post by chadeldridge on 2008-12-12
I may be doing something wrong, but I am unable to get this to work at all.

First of all i have to include python before the command and after i load the daemon i cannot load the app without errors.

---

### Post by iggykoopa on 2008-12-12
what errors are you getting when you try to load the app?

edit: also after you load the daemon what does
```

cat /var/log/wattospm/log

```
say?

---

### Post by chadeldridge on 2008-12-13
I dont even have that dir until /var/logs ... so something more major is wrong it seems.  Do you still need to run the installer or just run the app directly?

Running the installer i get:
```
chad@laptop:~/wattospm$ sudo python ./installer.py install
chmod: cannot access `/bin/wattospm.py': No such file or directory
chmod: cannot access `/bin/wattospm-daemon.py': No such file or directory
groupadd: group powermanagers exists
chad@laptop:~/wattospm$ 

```

---

### Post by iggykoopa on 2008-12-13
ok it looks like you have an old version of the installer because I'm having it install the program into /usr/bin now. try deleteing your wattospm directory, then get the newest svn and run the installer again.

---

### Post by chadeldridge on 2008-12-13
I did that just before writing ... i have version 31 checked out.

---

### Post by felipefoz on 2008-12-13
> **iggykoopa said:**
> ok it looks like you have an old version of the installer because I'm having it install the program into /usr/bin now. try deleteing your wattospm directory, then get the newest svn and run the installer again.

Iggy, there is something wrong with the installer, line 38, there must be corrected for /usr/bin, it is /bin/
I corrected that and it installed fine, I ran the daemonm, but the app was impossible to run without being superuser, there was a permission error with /etc/wattospm/config. Anyways, after rebooting the machine, it worked fine, (???) and now it's running as you've told us.

---

### Post by chadeldridge on 2008-12-13
Even after editing that line i still get this:

```
sudo python installer.py install
chmod: cannot access `/bin/wattospm-daemon.py': No such file or directory
groupadd: group powermanagers exists

```


EDIT:  nevermind i found the error for the one in the installer down a few more lines in the chmod section.  changed /bin/ to /usr/bin/

[COLOR="Silver"]Now i can run the app but i get no detected defaults.  The first screen is actually completely blank.
[/COLOR]

Looks like there is permission issues in the configs as well.  Here is the default:```
-rwxrwx--- 1 root powermanagers 2469 2008-12-13 08:41 config
-rw-r--r-- 1 root root          2469 2008-12-13 08:39 config.default

```

Ok .. i see something I was doing wrong.  I have all this time been running the wattospm.py file from the SVN directory when i should have been running it from /usr/bin/.  Mine now starts up and runs fine and the info is displayed on the first page.

---

### Post by chadeldridge on 2008-12-13
> Anyways, after rebooting the machine, it worked fine, (???) and now it's running as you've told us.


I am guessing because you have to log out and back in to get your username to recognize the addition to the powermanagers group.

---

### Post by iggykoopa on 2008-12-13
ok fixed the problem with the installer. Your still going to get one or two errors from it because I had to put in lines to remove the old versions, if they are already removed for you then it may give you an error message. Once it's installed it shouldnt matter where its run from as long as you use
sudo wattospm-daemon.py
wattospm.py
because the autodetection stuff is run by root now it won't find your username anymore. I just noticed it last night, I might have the installer find it.

---

### Post by chadeldridge on 2008-12-13
That did it .. thanks.

---

### Post by iggykoopa on 2008-12-13
got the init script written for it, it's in svn now. I'll post updated installation instructions in a minute.

---

### Post by iggykoopa on 2008-12-13
to download the svn version run this in a terminal:
```

svn checkout http://wattospm.googlecode.com/svn/trunk/ wattospm 
cd wattospm
sudo python installer.py install

```
it will add you to the powermanagers group and set the daemon to start at startup. youll have to restart the computer after the install.to run the gui use:
```

wattospm.py

```
you can also add the gui to start automatically by going to preferences->sessions and adding wattospm.py there. If you want to stop the daemon type:
```

sudo /etc/init.d/wattospm-daemon stop

```
the daemon logs to /var/log/wattospm/log. If you want to uninstall type(from the svn directory):
```

sudo python installer.py uninstall

```
When a new version comes out in svn just run the installer again, it'll remove the old version and install the new(it'll also remove your config but it's easy to set back up).

---

### Post by chadeldridge on 2008-12-13
Great great job it runs great now.  2 issues though.  The autodetect for username, network card, and cd drive does not work.  Also detection of battery or AC state does not seem to work on my machine.

LOG:

```
[(2008, 12, 13, 16, 57, 53, 5, 348, 0)] daemon started[(2008, 12, 13, 16, 58, 3, 5, 348, 0)]hdparm: 
/dev/sda:
 setting Advanced Power Management level to 0xc8 (200)
 setting acoustic management to 254
 setting drive write-caching to 1 (on)
 setting standby to 240 (20 minutes)
 write-caching =  1 (on)
 acoustic      = 254 (128=quiet ... 254=fast)
iwl wifi: 
intel sound: 
multi-core scheduling: 
thermal polling: [(2008, 12, 13, 17, 7, 8, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 10, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 11, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 12, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 13, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 14, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 16, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 17, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 18, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 19, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 20, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 21, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 22, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 23, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 24, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 25, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 26, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 27, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 28, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 29, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 31, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 32, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 33, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 34, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 35, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 36, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 37, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 38, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 39, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 40, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 41, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 42, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 43, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 44, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 45, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 46, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 47, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 48, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 49, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 50, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 52, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 53, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 54, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 55, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 56, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 57, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 58, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 7, 59, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 0, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 1, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 2, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 3, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 4, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 5, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 6, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 7, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 8, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 10, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 11, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 13, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 14, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 15, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 16, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 17, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 18, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 19, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 20, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 21, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 22, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 23, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 24, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 25, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 26, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 27, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 28, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 29, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 30, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 31, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 32, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 33, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 34, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 36, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 37, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 38, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 39, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 40, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 41, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 42, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 43, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 44, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 45, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 46, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 47, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 48, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 49, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 50, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 51, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 52, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 53, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 54, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 55, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 56, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 57, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 8, 59, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 0, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 1, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 2, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 3, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 4, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 5, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 6, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 7, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 8, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 10, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 11, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 12, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 13, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 14, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 15, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 16, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 17, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 18, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 19, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 21, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 22, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 23, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 24, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 25, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 26, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 27, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 28, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 29, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 30, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 31, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 32, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 33, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 34, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 35, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 36, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 37, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 38, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 39, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 40, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 41, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 42, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 44, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 45, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 46, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 47, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 48, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 49, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 50, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 51, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 52, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 53, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 54, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 55, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 56, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 57, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 58, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 9, 59, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 0, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 1, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 2, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 4, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 5, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 6, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 7, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 8, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 10, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 11, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 12, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 13, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 14, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 15, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 16, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 17, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 18, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 19, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 20, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 21, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 22, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 23, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 24, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 26, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 27, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 28, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 29, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 30, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 31, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 32, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 33, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 34, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 35, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 36, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 37, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 38, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 39, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 40, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 41, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 42, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 43, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 44, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 45, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 46, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 48, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 49, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 50, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 51, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 52, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 53, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 54, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 55, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 56, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 57, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 58, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 10, 59, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 0, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 1, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 2, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 3, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 4, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 5, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 6, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 7, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 10, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 11, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 12, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 13, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 14, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 15, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 16, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 17, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 18, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 19, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 20, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 21, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 22, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 23, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 24, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 25, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 26, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 27, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 29, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 30, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 31, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 32, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 33, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 34, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 35, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 36, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 37, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 38, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 39, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 40, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 41, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 42, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 43, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 44, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 45, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 46, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 47, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 48, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 49, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 50, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 52, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 53, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 54, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 55, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 56, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 57, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 58, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 11, 59, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 0, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 1, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 2, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 3, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 4, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 5, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 6, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 7, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 8, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent[(2008, 12, 13, 17, 12, 9, 5, 348, 0)]iwl wifi: 
intel sound: 
multi-core scheduling: 
firewire: 


thermal polling: sh: cannot create /proc/acpi/thermal_zone//polling_frequency: Directory nonexistent
```

---

### Post by iggykoopa on 2008-12-13
username autodetect doesn't work anymore because the daemon, I may add it to the installer, but you only need it for the ati and nvidia stuff. CD-Rom should still be working, I'll look into why it doesn't. With the network card is it the interfaces section? or is it for the iwl stuff? Also from your log it looks like the thermal polling part has an extra slash, I'll look into that too when I get home.

Do you guy's think I should remove the advanced/basic portion and just have it be advanced? I wanted it to be safer for beginners, but for me it's just annoying.

edit: also can you post the output of
```

cat /proc/acpi/battery

```

it's for the battery autodection stuff.

---

### Post by chadeldridge on 2008-12-13
I would think that you should just remove basic and just go all advanced.

Here is the output .. only my directory goes a bit deeper:

```
/proc/acpi/battery/BAT0$ cat info 
present:                 yes
design capacity:         7200 mAh
last full capacity:      7200 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 720 mAh
design capacity low:     218 mAh
capacity granularity 1:  72 mAh
capacity granularity 2:  72 mAh
model number:            DELL F51267
serial number:           860
battery type:            LION
OEM info:                Sanyo

```

The interfaces section i mean is in the General section.

---

### Post by iggykoopa on 2008-12-13
I'll look into it when I get home, at a friends house now. With the battery stuff is it set to auto not manual?

---

### Post by chadeldridge on 2008-12-13
correct this is set to auto.  Also i just noticed that i cannot get into the setting now without switching it to manual then i can single click the icon to bring up the settings again.

Sorry .. just keeping you up on the issues.


EDIT:  Actually i cant bring up the settings at all now ..

---

### Post by iggykoopa on 2008-12-13
ok thats weird... I'll look into it. The default settings put it in basic mode, you have to switched it to advanced to bring up the options...once you do that it should be fine though, when I get home I'll remove the basic stuff and see if that helps.

---

### Post by iggykoopa on 2008-12-13
I removed the basic mode. Also found why it wasn't letting you set it back to auto, it was calling a function I had separated into the daemon, it's fixed now.

---

### Post by chadeldridge on 2008-12-13
Much much better .. things act as I anticipate they should.  Interfaces on General tab still does not detect all my interfaces, but i can add them manually for now.

Thanks again.

---

### Post by iggykoopa on 2008-12-14
can you check if the nvidia portion is working correctly again? make sure you put in your user name, then to check if it is working open gconf-editor and go to apps->compiz->general->screen0->options when you change from powersaving and performance it should check and uncheck sync_to_vblank. It's working again for me now so I just wanted to check if it was working for anyone else.

---

### Post by chadeldridge on 2008-12-14
Confirmed .. Powersave unchecks it .. Performance checks it.

Good work.

However the setting is not changing in nvidia-settings, only in compiz.  Is this intended?

---

### Post by iggykoopa on 2008-12-14
correct, the guide I followed (vor's powersaving thread) just had that section, it only saves power if your actually using compiz. Still need to add in the xorg.conf stuff now to enable the generic nvidia power savings, maybe I'll put it in the installer since its a one time thing.

edit: as far as I know there isn't a cli equivelent to nvidia-settings. if you know a way to change them without the gui let me know and I can add it in.

---

### Post by chadeldridge on 2008-12-14
That would be awsome .. whenever you need more tested just yell.

---

### Post by chadeldridge on 2008-12-14
Iggy .. it looks like the Tacker option does not save if you click it.  Just something to look at when you get a chance.

---

### Post by iggykoopa on 2008-12-14
ok tracker bug is fixed now. I don't use that option so hadn't caught it.

---

### Post by chadeldridge on 2008-12-14
Installer is also not auto-updating from SVN.  I am doing it manually stil then running the installer.

Chad

---

### Post by chadeldridge on 2008-12-14
Installer is also not auto-updating from SVN.  I am doing it manually stil then running the installer.

Chad

---

### Post by iggykoopa on 2008-12-14
actually the installer wasn't intended to update automatically but thats a good idea...I'll have to add it in.

edit: also stop the daemon before you do a new install sudo /etc/init.d/wattospm-daemon stop. Then after the install.. sudo /etc/init.d/wattospm-daemon start (if you've installed before and are already in the powermanagers group you don't need to restart)

---

### Post by iggykoopa on 2008-12-14
ok I added an update option to the installer. checkout the newest svn then after that run:
```

sudo python installer.py update

```
and it should handle everything for you.

---

### Post by iggykoopa on 2008-12-15
if you use conky I wrote a script to monitor your power usage so you don't have to fire up powertop..instructions are here [http://crunchbanglinux.org/forums/topic/323/conky-power-usage-script/](http://crunchbanglinux.org/forums/topic/323/conky-power-usage-script/)

also I found a bug in the daemon that it is constanly changing the power mode even though it is already set, I'll track down why it's doing it tomorrow, but for now it's going to keep your disk spun up more because it is writing to the log constantly, it's only when you have it set to manual mode so for now just keep it on auto.

---

### Post by chadeldridge on 2008-12-16
iggy:  I was able to reproduce the error you spoke of above.  Also I have been playing with FF some and have had luck with moving its browser.cache to a ram disk, i get fewer wakeups at least.

---

### Post by iggykoopa on 2008-12-16
I was gonna fix that last night but my mini 9 came in so I had to play around with it. I actually already wrote a launcher for firefox that loads your profile into ramdisk, just need to integrate it into the gui.

edit: the launcher actually moves the whole ~/.mozilla/firefox directory into ramdisk because one of the files it syncs (it's a sqlite database) is in that directory and it cuts down even more on writes.

---

### Post by chadeldridge on 2008-12-16
You will have to give me your feelings on the Mini as well, this beast M1710 is killing me to carry around.  I almost ordered the MSI Wind, but then played with it in store and was not impressed.  If the Dell Mini is good I will probably get one also.

---

### Post by iggykoopa on 2008-12-16
heres a quick writeup I did of it for the crunchbang forums [http://crunchbanglinux.org/forums/topic/336/dell-mini-9-review/](http://crunchbanglinux.org/forums/topic/336/dell-mini-9-review/) .

---

### Post by iggykoopa on 2008-12-16
fixed the bug with manual mode, it's in svn. Started integrating the firefox launcher, should be done tomorrow.

---

### Post by chadeldridge on 2008-12-17
Here is the output from

 ```
sudo python installer.py update
```

```
 * Stopping WattOS power manager daemon wattospm-daemon.py                      python /usr/bin/wattospm.py: No such file or directory
 Removing any system startup links for /etc/init.d/wattospm-daemon ...
   /etc/rc0.d/K20wattospm-daemon
   /etc/rc1.d/K20wattospm-daemon
   /etc/rc2.d/S20wattospm-daemon
   /etc/rc3.d/S20wattospm-daemon
   /etc/rc4.d/S20wattospm-daemon
   /etc/rc5.d/S20wattospm-daemon
   /etc/rc6.d/K20wattospm-daemon
 Adding system startup for /etc/init.d/wattospm-daemon ...
   /etc/rc0.d/K20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc1.d/K20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc6.d/K20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc2.d/S20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc3.d/S20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc4.d/S20wattospm-daemon -> ../init.d/wattospm-daemon
   /etc/rc5.d/S20wattospm-daemon -> ../init.d/wattospm-daemon
Traceback (most recent call last):
  File "installer.py", line 67, in <module>
    if arg == "update":
  File "installer.py", line 13, in update
    os.system("/etc/init.d/wattospm-daemon start")
  File "installer.py", line 59, in install
    os.system("chown root:powermanagers /etc/wattospm/config")
NameError: global name 'user' is not defined

```


Also the update feature erases all the settings for the app.  Might want to make it save them or give the option to manually save out your options and then restore once a new version is installed.  (or that could be what the installer failed at... i havent looked into the code yet)

---

### Post by iggykoopa on 2008-12-17
The reason I don't have it save your old config is if there are new options in the config file and you use the old one then the gui will not work correctly, I could try having it import your old settings into the new one though. I know where the installer is having an error, but I don't know why. Could you type in 
```

logname

```
in the terminal and see if it gives you back your username?

---

### Post by chadeldridge on 2008-12-17
That's a good point about the settings, i actually don't mind redoing them, but just thinking of a feature for down the road.

logname does return my username correctly.

One more issue now as well, after updating you cannot click the OK button inside the app or the button does nothing you can no longer save the settings.

---

### Post by iggykoopa on 2008-12-18
I think I fixed the problem with the installer, just haven't uploaded it yet as I'm still working on the firefox launcher. I couldn't reproduce your error with not being able to click ok, could you run wattospm.py from the terminal and see if you get any errors?

---

### Post by chadeldridge on 2008-12-18
It looks like it is complaining about not being able to open the config file:

```
 python wattospm.py 
Traceback (most recent call last):
  File "wattospm.py", line 530, in change_activation_mode
    Config.write(open("/etc/wattospm/config","w"))
IOError: [Errno 13] Permission denied: '/etc/wattospm/config'
```


And here would be why:

```
/etc/wattospm$ ls -l
total 8
-rw-r--r-- 1 root root 2497 2008-12-18 09:39 config
-rw-r--r-- 1 root root 2456 2008-12-17 07:37 config.default

```

Looks like when the installer ran last it created the files as root and not as the correct user.

---

### Post by chadeldridge on 2008-12-18
Just a question:  Is the utility doing anything to the eth0 controller after a switch to battery is detected.  For some reason once i go to battery mode my giga network connection disconnects and then reconnects locked at 100mb.  The only way to get back to giga is to reboot with the power connected.  Going from battery to AC does not do a similar disconnect of the card, only ac to battery.

---

### Post by iggykoopa on 2008-12-18
Well that explains it for the config file, when you tried updateing last it failed on the step before the one that chowns the config file to the powermanagers group.
For the ethernet connection theres nothing that should effect it, you could try turning off any options in the modules section and see if that helps(they're bluetooth, usb, and firewire but you never know) and checking dmesg when you unplug it.

---

### Post by felipefoz on 2008-12-18
I did a fresh install here.
The program didn't recognize neither the username nor the cd-rom drive. it used to do it before.
The other things are running fine here.
What about that option of taking down the ethernet interface?
My eth0 wakes up a lot my processor! :)

---

### Post by iggykoopa on 2008-12-18
I'll add the username detection into the installer, it doesn't work right with the daemon that's why I took it out. I'll take another look at the cd-rom but it was still working for me. I was working on the option for taking down network devices but stopped when I seperated it into the gui and daemon, still working out the bugs on that and adding a firefox launcher, once I get that stuff done I'll start working on it again.

---

### Post by chadeldridge on 2008-12-18
Your work on this is awesome, thanks again.

---

### Post by iggykoopa on 2008-12-19
I added back in username autodetection and hopefully fixed the error you were having with the updater, you'll have to update this time manually though. Added the firefox launcher, but be careful with it. Make sure you close firefox before you turn off the machine or it won't restore your profile (it makes a backup and will restore from that the next time you launch firefox) also you need rsync installed first, I think it's installed by default now though. I'll try to get to the network interface options tomorrow.

edit: thanks chadeldridge I'm having fun working on this, and I appreciate the troubleshooting

edit again: ok tested out the firefox launcher more, it works if you start wattospm.py from the terminal... but for some reason it doesn't work right otherwise

---

### Post by felipefoz on 2008-12-19
> **chadeldridge said:**
> Your work on this is awesome, thanks again.

Yep
iggykoopa, you are definitely doing a great job building this GUI, I am gonna use this moment to say thanks as well.

---

### Post by chadeldridge on 2008-12-19
FYI .. after manual checkout from SVN and running the installer:


```
sudo python installer.py install
[sudo] password for chad: 
 Removing any system startup links for /etc/init.d/wattospm-daemon ...
   /etc/rc0.d/K20wattospm-daemon
   /etc/rc1.d/K20wattospm-daemon
   /etc/rc2.d/S20wattospm-daemon
   /etc/rc3.d/S20wattospm-daemon
   /etc/rc4.d/S20wattospm-daemon
   /etc/rc5.d/S20wattospm-daemon
   /etc/rc6.d/K20wattospm-daemon
Traceback (most recent call last):
  File "installer.py", line 116, in <module>
    install("new")
  File "installer.py", line 82, in install
    shutil.copy("firelaunch.py","/usr/bin/firelaunch.py")
  File "/usr/lib/python2.5/shutil.py", line 85, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.5/shutil.py", line 51, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: 'firelaunch.py'

```

---

### Post by iggykoopa on 2008-12-19
wow I feel really stupid now, it was late when I uploaded that and forgot to add firelaunch.py to the repository. Well I think when I get home tonight I'm gonna just integrate that code into the gui itself, I don't want to be throwing a ton of files around everywhere. Also I may rename wattospm.py to just wattospm, the .py has kinda been bugging me. Any way sorry about that, I'll fix it tonight.

---

### Post by iggykoopa on 2008-12-19
ok I think I got everything fixed if you wanna give it another try.

---

### Post by chadeldridge on 2008-12-19
Downloaded and installed .. rebooting now.  I just removed my directory although im sure i didn't have to.  Wanted to start fresh.  I manually checked it out from svn and then did sudo python installer.py install.

OK so its up and running, still no cdrom detect, but userid detect did work fine.  Also if you meant it to be in this release i do not see any firefox options in the gui.

Ahh .. i see it now, you put it in the dropdown list for the gui.

---

### Post by iggykoopa on 2008-12-19
yeah I figured it would be used often enough that it would be annoying to have to open the configuration menu to launch firefox. Is it working ok for you?

edit: I'll have to wait a little to check on the cdrom stuff, my wifes on the other laptop and the mini doesn't have a cdrom drive.

---

### Post by iggykoopa on 2008-12-23
added a one time options tab, only thing in it now is interfaces up/down I know felipefoz was asking for this for a while though so here it is.

---

### Post by felipefoz on 2008-12-23
> **iggykoopa said:**
> added a one time options tab, only thing in it now is interfaces up/down I know felipefoz was asking for this for a while though so here it is.

Nice, thanks for this feature, it is going to be very useful.
So, yesterday I was listening to some music, and after a while, the app locked up. I don't know what happened, I needed to kill it and launch it again. Did you experience anything like that?

edit: The computer was idle, i wasn't in front of it while listening to music

---

### Post by iggykoopa on 2008-12-23
I actually have had that happen to me as well, but I haven't been able to track down what is causing it. I'm looking into it now, if you figure anything out about why it locks up let me know.

---

### Post by RookieUbuntuUser58 on 2008-12-23
Is this the same updated version that you helped me install in this thread (last couple of posts in the thread). 

[http://ubuntuforums.org/showthread.php?t=995814&page=4]("http://ubuntuforums.org/showthread.php?t=995814&page=4") 

One problem I'm having is sometimes when I click on the icon nothing happens, can't switch modes. No options or nothing. Sometimes it works other times it doesn't. Any ideas?

---

### Post by iggykoopa on 2008-12-23
you could try running wattospm.py from a terminal instead of hitting alt+f2 and see if it gives you any errors. There is a problem that was just noticed with it lockign up occasionally, that may be whats happening to you, I'm looking into but not sure what is causing it yet. By default it is set on pretty safe options, but you wont get as much powersaving as possible. Go into the configuration screen (left click on the icon) and enable settings that are checked as detected, you'll probably want to google the settings to make sure you know what they do until I get the documentation done for it. a good site which has explanations for most of the options is [www.lesswatts.org](www.lesswatts.org) .

---

### Post by RookieUbuntuUser58 on 2008-12-23
> **iggykoopa said:**
> you could try running wattospm.py from a terminal instead of hitting alt+f2 and see if it gives you any errors. There is a problem that was just noticed with it lockign up occasionally, that may be whats happening to you, I'm looking into but not sure what is causing it yet. By default it is set on pretty safe options, but you wont get as much powersaving as possible. Go into the configuration screen (left click on the icon) and enable settings that are checked as detected, you'll probably want to google the settings to make sure you know what they do until I get the documentation done for it. a good site which has explanations for most of the options is [www.lesswatts.org](www.lesswatts.org) .

No errors when I run wattospm.py in the terminal. It loads another icon, this one in which I can click on and change settings. But I still have the other icon (same as one that just loaded) in my notification area, which when I click nothing happens. Any ideas how to get rid of that icon since I can't right click and get rid of it?


Edit : When I close the terminal the working icon disappears leaving the one that doesn't work.

---

### Post by iggykoopa on 2008-12-23
to get rid of the old one use alt+f2 then when that pops up type in 
```

killall wattospm.py

```
that will get rid of any running copies, then just start it up again. Hopefully I can figure out whats making it lock up soon and fix it. When it locks up though the daemon (what actually changes the settings) will still be working fine, you just won't be able to change settings or get notified when it changes modes.

---

### Post by RookieUbuntuUser58 on 2008-12-23
Thanks for the help.

---

### Post by RookieUbuntuUser58 on 2008-12-23
> **iggykoopa said:**
> to get rid of the old one use alt+f2 then when that pops up type in 
```

killall wattospm.py

```
that will get rid of any running copies, then just start it up again. Hopefully I can figure out whats making it lock up soon and fix it. When it locks up though the daemon (what actually changes the settings) will still be working fine, you just won't be able to change settings or get notified when it changes modes.

Just tried to delete it using your method, didnt work. Then I typed that code into a terminal and it said wattospm.py: no process killed.

---

### Post by iggykoopa on 2008-12-23
it may have been launched as python wattospm.py or something similar, the name needs to match exactly, another way to kill it is.
```

ps aux | grep wattospm

```
you will get output similar to this
```

root         2  0.0  0.0      0     0 ?        S<   Dec22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Dec22   0:00 [migration/0]

```
the first number is the PID you can use that to kill it, from the terminal
```

kill (the PID)

```
no parenthesis or anything. i.e. kill 2

---

### Post by RookieUbuntuUser58 on 2008-12-23
I ended up uninstalling the whole program and reinstalling (using the guide on the 1st post). That got rid of the non-working icon and now I have one that actually works and isn't frozen on the screen.

---

### Post by iggykoopa on 2008-12-23
ok I did find one bug that I fixed, it wasn't saving the ipw wireless information correctly. Even if you didn't enable ipw once you hit ok after making changes it wouldn't allow you to open the config window again. So go grab the latest svn. If you still find it locking up on you let me know, I still don't think I've resolved that issue, but we'll see.

---

### Post by felipefoz on 2008-12-24
@iggykoopa

Hey, I was just figuring out, I use this another program emesene to use the msn messenger network, and it uses a lot the disk, like firefox, what steps should I do to do a launcher just like you did for firefox?

---

### Post by iggykoopa on 2008-12-24
if you want to try to figure it out yourself, around line 500 is the class firelauncher, you'll need to copy that section and modify it. If you want me to look into it I could try to make the launcher code more modular so it is easier to launch other applications as well.

---

### Post by chadeldridge on 2008-12-24
I just upgraded and had the same issue, unable to lauch the app from the tray icon.  I had to uninstall and then reinstall to fix it.  Have it back up and running now, but CDrom detect and Interface detect all failed.

Also left click is producing this error:

```
chad@chad-laptop:~/wattospm$ python wattospm.py 
Traceback (most recent call last):
  File "wattospm.py", line 670, in on_left_click
    Preferences = advPrefs() 
  File "wattospm.py", line 181, in __init__
    self.readSettings()
  File "wattospm.py", line 258, in readSettings
    self.IPWCombo.set_active(self.ipw_interfaces.index(Config.get("ipw_wifi","interface")))
ValueError: list.index(x): x not in list
Traceback (most recent call last):

```

Manual mode switch does work, but it rolls back to automatic after a few seconds.

---

### Post by iggykoopa on 2008-12-24
I'll have to look more into the cdrom autodetection, right now it's using hal find device by capability. It isn't working correct on my mini either, I don't have a cdrom drive and it detects a ton of stuff, like /dev/snd lol. With the interfaces and bluetooth they need to be up for it to detect them, are the interfaces it's not detecting up at the time?

edit: make sure you close wattospm.py and stop the daemon before you upgrade then start them again, the error your getting is the bug I just fixed. It shouldn't be doing it anymore. If it's still doing it maybe I didn't fix it good enough ;)

---

### Post by chadeldridge on 2008-12-24
Yes they are up, acutally using them both right now.

---

### Post by iggykoopa on 2008-12-24
is the interfaces section just blank? or is it not detecting all of them?

---

### Post by chadeldridge on 2008-12-24
Nope, just have lo.

---

### Post by iggykoopa on 2008-12-24
that's weird, the autodetection works by taking your ifconfig and parsing the output of that. Thats why the interface needs to be up, but if it's finding lo it should find the others. Do you mind posting your ifconfig?

---

### Post by chadeldridge on 2008-12-24
Bluetooth is down right now, but here id the rest.


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:0f:eb:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.5 KB)  TX bytes:1500 (1.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:09:81:73  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe09:8173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3861893 (3.8 MB)  TX bytes:620254 (620.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-81-73-31-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by iggykoopa on 2008-12-24
ok I think I fixed the interface detection part. Give it a try now, also I changed the cdrom drive detection part but I'm not sure if it will fix your issue, if it doesn't could you run
```

hal-find-by-capability --capability storage.cdrom

```
and tell me the output?

---

### Post by felipefoz on 2008-12-24
> **iggykoopa said:**
> if you want to try to figure it out yourself, around line 500 is the class firelauncher, you'll need to copy that section and modify it. If you want me to look into it I could try to make the launcher code more modular so it is easier to launch other applications as well.

Okay, I'll give it a try. Don't bother making easier to launch it to another applications. You can put it on far future to do list. hehe
Just installed revision 46, fresh install, working fine, cd-rom detects, interfaces detects, also tested. 
Bluetooth is being detected,  although I don't even have the service here, isn't something linked with the uhci_hcd, which is also used for usb?

---

### Post by iggykoopa on 2008-12-24
some of the bluetooth stuff depends on uhci (which is for usb) so you need to remove uhci before you can remove bluetooth. And it uses hciconfig to detect bluetooth so that may be why it is detecting something for you.

---

### Post by felipefoz on 2008-12-24
> **iggykoopa said:**
> some of the bluetooth stuff depends on uhci (which is for usb) so you need to remove uhci before you can remove bluetooth. And it uses hciconfig to detect bluetooth so that may be why it is detecting something for you.

Hum, so it uses hciconfig, I was just checking that I don't have installed hciconfig, as I uninstalled all bluetooth support as I don't have it. When the program tries to detect bluetooth through hciconfig, it doesn't find because it is uninstalled and somehow it detects it.

---

### Post by felipefoz on 2008-12-24
I was researching about brightness here
I found out that gnome-power-manager also uses hal (one of the ways) to detect and change the lcd brightness.
here I typed
```
$ lshal | grep video
  system.hardware.primary_video.product = 1331  (0x533)  (int)
  system.hardware.primary_video.vendor = 4318  (0x10de)  (int)
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'  (string)
  input.keymap.data = {'e025:help', 'e026:setup', 'e027:battery', 'e029:switchvideomode', 'e033:euro', 'e034:dollar', 'e054:bluetooth', 'e055:wlan', 'e056:wlan', 'e057:bluetooth', 'e058:bluetooth', 'e059:brightnessup', 'e06e:brightnessup', 'e06f:brightnessdown', 'e071:f22', 'e072:f22', 'e073:prog2', 'e074:prog1', 'e075:presentation', 'e078:fn', 'e079:f23'} (string list)
  info.linux.driver = 'uvcvideo'  (string)
  info.linux.driver = 'uvcvideo'  (string)
udi = '/org/freedesktop/Hal/devices/usb_device_64e_a101_CN0314_OV03_VA_R02_00_00_if0_video4linux'
  access_control.file = '/dev/video0'  (string)
  access_control.type = 'video4linux'  (string)
  info.capabilities = {'video4linux', 'video4linux.video_capture', 'access_control'} (string list)
  info.category = 'video4linux'  (string)
  info.subsystem = 'video4linux'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a101_CN0314_OV03_VA_R02_00_00_if0_video4linux'  (string)
  linux.device_file = '/dev/video0'  (string)
  linux.subsystem = 'video4linux'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/video4linux/video0'  (string)
  video4linux.device = '/dev/video0'  (string)
  video4linux.version = '1'  (string)

```
Then I found another way to change brightness (0 to 9), in the third line, listing the video path. 
```
echo 9 > /sys/devices/virtual/backlight/acpi_video0/brightness
```
another way by me, is using the /proc/ but it is far more complicated to get to the folder, as you already know
I'd suggest to have a look into it.
cheers
merry xmas to all

edit: I didn't figure out yet, but gpm uses dbus to send a message to hal, to change brightness, hal also provides information on how many levels of brightness is supported, etc...

---

### Post by iggykoopa on 2008-12-24
that explains why it detects bluetooth for you, I wasn't checking if hciconfig is installed, just wether there was a response from it. Since you don't have it installed it responds that it isn't installed, so the program thinks you have devices. I'll add in a check if you have it installed when I get a chance. I'll look into the brightness control as well.

---

### Post by iggykoopa on 2008-12-25
ok uploaded new version, it checks if bluez-utils is installed before checking for bluetooth devices.

---

### Post by felipefoz on 2008-12-25
> **iggykoopa said:**
> ok uploaded new version, it checks if bluez-utils is installed before checking for bluetooth devices.

working as desired!!! :)

---

### Post by felipefoz on 2008-12-27
I was monitoring the disk writes with iotop, and I noticed that gconf, and kjournald use the disk a lot, preventing from spinning down. From gconf I didn't come out with a solution, but with kjournald I figured out that the journal commit should be applied also to the /home partition, now is being only applied to the root partition, as the both partitions are in the same HD, it's pointless setting a higher journal commit to only one partition. Is there anyway to add, maybe a comma, another partition after the root one??

---

### Post by iggykoopa on 2008-12-27
I can add that in sometime, I was trying to make it as easy to use for beginners as I could so I figured most of them would have the same partition for / and home. Also I noticed the writes with gconf, I could set up something like the firefox launcher with gconf, but it is kinda bad to mess with, all you would lose is configuration settings but it wouldn,t be fun to set all that back up.
It may be a little bit, I've been hooked on deathnote and I'm getting ready to move to germany. Speaking of that if there are any new features anyone wants let me know in the next two weeks, I'm moving in about a month and after that it'll be two to three months before I'll be able to really work on the gui again.

---

### Post by cheaptrick on 2009-01-04
hey i've right click on the icon and run firefox. Something wasnt quite right appeared on the terminal. Still, Firefox ran normally.

when i close it , i couldnt start firefox anymore. I get the message  "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system." appears everytime i try run it. 
According gnome-system-monitor, there isnt any firefox processed running in the background.

I've tried reinstalling firefox, but it doesnt help at all

---

### Post by chadeldridge on 2009-01-04
Just for giggles try to sudo killall firefox-bin and see what happens.

---

### Post by cheaptrick on 2009-01-04
0 kills..

---

### Post by iggykoopa on 2009-01-04
not all process's show up in gnome-system-monitor, try 
```

ps aux | grep firefox

```
if their really is a copy of firefox running it will show up then. If nothing shows up another thing to try is:
```

ls ~/.mozilla

```
if there is a firefoxbackup folder then try:
```

rm -R ~/.mozilla/firefox
mv ~/.mozilla/firefoxbackup ~/.mozilla/firefox

```
if that still doesn't work try going into synaptic and when you uninstall firefox mark it for complete removal then install it again. If it happens again the terminal output before it fails would help so I can figure out why it happened. 
The firefox launcher copies your firefox folder to firefoxbackup then copies it to your ramdisk, it removes the firefox folder then symlinks it to the copy in the ramdisk. Then it uses rsync every 5 minutes to sync the backup with the copy in ramdisk.

---

### Post by Ubun00btu on 2009-02-14
Hope this isn't a deceased thread yet, I'd really like to give this GUI/app a try on my M1330 that can take a battery out in 40 minutes.

I followed the instructions and when I attempt to start the program I get nothing.

I type "sudo wattospm.py" and "enter" and then nothing happens.  

Best of luck finishing the app, I'm really looking forward to using it.


EDIT:  Disregard.  I'm an idiot - it launched to the tray (which I've hidden due to using AWN and wanting a clean screen).  Thank you for making a great app!!!

---

### Post by iggykoopa on 2009-02-14
glad you like the gui, I will continue development on it, but I'm currently moving to germany so it may be a couple weeks before anything happens with it. If you have any problems just leave a bug report on the google code page or here and I'll be checking in every couple days if I can.

---

### Post by m4cph1sto on 2009-02-20
I've been using your gui for a few months and I think it's great! I have found 2 bugs to report:

- Some settings (HDPARM), maybe all, aren't remembered when I resume from suspend.  I have to change power state (e.g. plug in or remove the AC adapter) after resuming to get the proper settings.

- Manual switching of power modes usually doesn't work.  I can change it once, but then the gui seems to freeze and won't let me change back.

---

### Post by iggykoopa on 2009-02-21
Thanks for the reports, if you could file them on the google code page I would appreciate it, that way I won't forget about them while I'm on the way to germany. I'll take a look at them when I get a chance, but it may be a few weeks, hopefully by then though I can make another release with a few more features :D (and fix your bugs)

---

### Post by loomsen on 2009-04-02
Sup iggy.

You might remember I asked for an interface to set my battery load status to a custom level. Must have been somewhere around page 5 or so. However, you asked me to let you know if I stumble upon sth.

And well, finally I did. Unfortunately it's a driver module for my Laptop (Compal FL90) which creates exactly what I was looking for:

[[img]http://www.ubuntu-pics.de/thumb/11843/tuz_004__W0NrUh.png[/img]](http://www.ubuntu-pics.de/bild/11843/tuz_004__W0NrUh.png)

Maybe it's possible to create something similar generic?

Just wanted to let you know... L8r

---

### Post by iggykoopa on 2009-04-02
I can look into it again, I'll have to find out if the driver uses something hardware specific or if it's some type of acpi call I can use or something. Thanks for pointing it out.

---

### Post by iggykoopa on 2009-07-14
well I've finally got back to working on wattospm, new update to svn should fix the issues with xbacklight. I'll start looking back into the issues you guys reported now that I'm settled into my house in germany.

---

### Post by felipefoz on 2009-07-15
Welcome back...
If you have any news, let us know...
As you know, there are many people that want to help...
cheers..


> **iggykoopa said:**
> well I've finally got back to working on wattospm, new update to svn should fix the issues with xbacklight. I'll start looking back into the issues you guys reported now that I'm settled into my house in germany.

---

### Post by iggykoopa on 2009-07-15
Thanks right now I'm working on a power usage graph...should have it working in a little while. If you could test if xbacklight is working for you now it would help. it's not on my dev machine because KMS on intel video cards breaks xbacklight(running 9.10 right now).

---

