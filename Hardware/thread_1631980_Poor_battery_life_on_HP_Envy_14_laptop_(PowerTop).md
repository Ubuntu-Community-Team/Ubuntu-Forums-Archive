---
title: "Poor battery life on HP Envy 14 laptop (PowerTop)"
date: 2010-11-27
forum: Hardware
---

### Post by mpdava on 2010-11-27
I use Ubuntu 10.10 and I only get 2 hours battery life. On Windows 7, it runs up to 4 hours. I believe there is a problem with USB auto-suspend as PowerTop shows USB being active 100% of time.

Full PowerTop dump is attached.

Please let me know if you have any suggestions? Thank you.

-------
A USB device is active 100.0% of the time:

/sys/bus/usb/devices/1-1

Suggestion: Enable Device Power Management by pressing the P key

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key

Suggestion: Enable SATA ALPM link power management via:

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

or press the S key.

Suggestion: Enable the CONFIG_PM_ADVANCED_DEBUG kernel configuration option.

This option will allow PowerTOP to collect runtime power management statistics.

Recent USB suspend statistics

Active Device name

100.0% USB device 2-1.6 : HP Webcam (Bison Electronics Inc.)

100.0% USB device 1-1.3 : HP Integrated Module (Broadcom Corp)

100.0% /sys/bus/usb/devices/2-1

100.0% /sys/bus/usb/devices/1-1

100.0% USB device usb2 : EHCI Host Controller (Linux 2.6.35-23-generic ehci_hcd)

100.0% USB device usb1 : EHCI Host Controller (Linux 2.6.35-23-generic ehci_hcd)

---

### Post by guakeke on 2010-11-27
Hi there, I am also running 10.10 on the Envy 14 and managed to improve my battery life considerably by switching off the ATI graphics card as detailed here: 

[http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/](http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/)

Good luck!

---

### Post by mpdava on 2010-11-27
I actually did that step and I only use the internal Intel i915 video card. ATI card is switched off, I have a script that runs at startup and adds:
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

I would be curious to know how many hours you get with your Envy14?  Do you have the same 100% usb usage with powertop (sudo powertop -d)? Not sure why I only get 2hours and this is with 30% LCD backlight. I run Ubuntu 10.10 - x64 Thanks!

---

### Post by guakeke on 2010-11-27
Hi there mpdava,

I just ran PowerTop and got the same result:

A USB device is active 100.0% of the time:
/sys/bus/usb/devices/1-1

I am running those same scripts at start up. I'll time my battery life and get back to you again.

---

### Post by guakeke on 2010-11-27
I've just clocked up 2 hrs 15 mins with the wireless connection on and the backlight at 30%, 32-bit 10.10, so I guess we are in a similar situation.

I'm completely new to Linux, so I'd appreciate any more tips that come to light.

Thanks.

---

### Post by mpdava on 2010-11-29
Thanks [guakeke]("http://ubuntuforums.org/member.php?u=1158264") for checking. I did another test at my end and the battery lasted about 2h:20min. It is definitely a problem as on Windows 7 I get close to 4 hours (I dual boot Ubuntu and Windows 7). I will keep looking and let you know if I find a resolution.
 
FYI: Not related, here are the customizations I did so far to make Ubuntu run better with Envy 14:
 
 1. Add to “rc.local”
 # Enable on demand CPU performance
 echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  
 echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  
 echo ondemand > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  
 echo ondemand > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  
 echo 1 > /sys/devices/system/cpu/sched_mc_power_savings  
 
 # Enable power management for the sound card
 echo 1 > /sys/module/snd_hda_intel/parameters/power_save  
 
 # Power saving for the file system
 sudo echo 1500 > /proc/sys/vm/dirty_writeback_centisecs  
 
# By default LCD bringhtness is 0 so the screen is blank at startup. Just add this line to start your laptop # with 30% LCD brightness.  
 echo 3 > /sys/class/backlight/acpi_video0/brightness  
 
 # Change the owner of this file to your “username” so you can turn off ATI card once Gnome is loaded
 chown username /sys/kernel/debug/vgaswitcheroo/switch
  
2. When Gnome is loaded, I call another script “switch_to_integrated.sh” to turn off ATI card
 echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
 echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
 
 3. Touchpad changes. I find that the touchpad is jumping around like crazy when you touch it with two fingers. Here are my changes that fix the issue almost 100%.
 
- Download and install this package that adds multitouch support:
 [https://launchpad.net/~utouch-team/+archive/utouch/+build/2049547]("https://launchpad.net/%7Eutouch-team/+archive/utouch/+build/2049547")
 
- Add to “/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf”
 Section "InputClass"  
         Identifier "touchpad catchall"  
         MatchProduct "SynPS/2 Synaptics TouchPad"  
         MatchIsTouchpad "on"  
         Driver "synaptics"  
         # this takes care of the jumpy cursor
         Option "JumpyCursorThreshold"  "250"  
         # enable right click at the far bottom right of the touchpad
         Option "TapButton2" "3"  
         # detect palm touches  
         Option "PalmDetect" "on"  
         # lock mouse on window when dragging
         Option "LockedDrags" "1"  
         # increase mouse Min and Max speed from default
         Option "MinSpeed" "0.7"  
         Option "MaxSpeed" "1.0"  
 EndSection  
  
 You can simulate  right click with a two fingers tap or one finger tap on the bottom-right corner. Also under Preferences->Mouse, I now have an option for two fingers scrolling or only edge scrolling. For more options check out “synclient -l”

---

### Post by guakeke on 2010-11-30
Hi mpdava,

This is super stuff thank you for sharing.

I have made those changes to my rc.local file and I can confirm that my backlight now comes on at login and the dedicated graphics powers down. My Linux skills aren't up to confirming the other improvements but they are greatly appreciated nevertheless.

Just for the record, I got my Clickpad working using this package:

xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb 

It's available here [http://sites.google.com/site/andyeyre/files](http://sites.google.com/site/andyeyre/files)

It enables side-scrolling, tap to click, right click and tap to right click in the bottom right hand of the Clickpad.

---

### Post by mpdava on 2010-12-12
Thanks, I tried the package and it works great! 

Another thing I had problems with was very slow network performance when running on battery. The fix is to create an empty file called "wireless" and place it in /etc/pm/power.d/  (link [http://uselessuseofcat.com/?p=67](http://uselessuseofcat.com/?p=67))

Also Flash video was slow or freeze in full screen mode. I found these commands on the web and now Flash is as good as Windows. 

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
 
I'm still looking for a solution for the battery life ....

---

### Post by guakeke on 2010-12-13
Hi mpdava,

Glad the package worked for you, that's good news. 

I also found flash video froze in full screen mode, however I can confirm your fix works for me.

I haven't noticed any problem with slow network performance on battery.

Thanks a lot for sharing your expertise, it has made a real difference to what is my first experience running Ubuntu!

---

### Post by luddis on 2010-12-24
> **guakeke said:**
> 

Just for the record, I got my Clickpad working using this package:

xserver-xorg-input-synaptics_1.2.2-2ubuntu5eyre1_i386.deb 

It's available here [http://sites.google.com/site/andyeyre/files](http://sites.google.com/site/andyeyre/files)

It enables side-scrolling, tap to click, right click and tap to right click in the bottom right hand of the Clickpad.

I happened to install the amd64 version of ubuntu and I cannot find any amd64.deb file in the link you gave and thus can't install the package. I suppose I have to resolve to the other solution on this thread then?

Thank's for all your tips anyway, and Merry Christmas!

---

### Post by mpdava on 2010-12-28
Please see:

[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.2.2-2ubuntu5/+build/1971162](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.2.2-2ubuntu5/+build/1971162)

it is the last link at the bottom.

---

### Post by Marc128000 on 2011-01-17
The poor battery life is definitely affected by the power state of the discrete graphics card. My blog has a step by step breakdown of using the switchable graphics to power down the GPU.
[[COLOR="DeepSkyBlue"]Linux on the Envy 14 - Switchable Graphics[/COLOR]]("http://linuxenvy.blogspot.com/2011/01/tackling-switchable-graphics.html")

---

### Post by socanpower on 2013-03-14
hp envy 14 battery Long Life Use And Maintenance Guide:
    1&#12289;If your side when there is AC power, the boot of the day before the first AC power supply connected to the laptop, to ensure that the battery lights and then boot! Keep this in mind! In this case, the battery is a slight current for charging, the motherboard power supply protection will not let the machine have any questions! The case of battery is not counting the number of charge cycles.
    2&#12289; When using a laptop as a desktop replacement the battery should not be left in for long periods of time. The laptop will over time discharge the battery. Remove the battery,making sure that it is charged to 90% and store it in a dry, cool place. Ensure that it is wrapped protectively and nothing will be dropped on it.
    3&#12289; The battery should be re-installed every 3-4 weeks and allowed to fully discharge. Leaving a battery in storage for longer than this without using could cause the battery to fully discharge as the circuitry of the battery itself consumes power.
    4&#12289;Leaving a battery in a laptop while using an electrical outlet for long periods of time will keep the battery in a constant state of charging up and that will reduce the life cycle of the battery.

---

### Post by overdrank on 2013-03-14
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

