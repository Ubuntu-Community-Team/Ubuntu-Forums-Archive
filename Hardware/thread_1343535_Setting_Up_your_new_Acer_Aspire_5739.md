---
title: "Setting Up your new Acer Aspire 5739"
date: 2009-12-01
forum: Hardware
---

### Post by TGArcher on 2009-12-01
So, recently I bought an Acer Aspire 5739 Notebook from a sweet deal on Newegg.com. Here are the specs they give:

**Model**
Brand 	          Acer
Series 	          Aspire
Model 	          AS5739G-6959
Part# 	          LX.PDR02.001

**General**
Operating System  Windows 7 Home Premium 64-bit
CPU Type 	  Intel Core 2 Duo T6600 2.2G
Screen 	15.6"
Memory Size 	  4GB DDR3
Hard Disk 	  320GB
Optical Drive 	  DVD Super Multi
Graphics Card 	  NVIDIA GeForce GT 130M
Video Memory 	  1024MB
Communication 	  Modem, Gigabit LAN and WLAN
Battery Life 	  Up to 2.5 hours
Dimensions 	  16.14" x 11.25" x 1.37" - 1.63"
Weight 	6.10 lbs.

**Other Features** 	  Fingerprint reader

**CPU**
CPU Type 	  Intel Core 2 Duo
CPU Speed 	  T6600(2.20GHz)
CPU FSB 	  800MHz
CPU L2 Cache 	  2MB
Chipset
Chipset 	  Intel PM45

**Display**
Screen Size 	  15.6"
Wide Screen Support 	Yes
Resolution 	  1366 x 768
LCD Features 	  LED backlight & Acer CineCrystal Technology

**Graphics**
GPU/VPU 	  NVIDIA GeForce GT 130M
Video Memory 	  1024MB Dedicated DDR2 VRAM
Graphic Type 	  Dedicated Card

**Hard Drive**
HDD 	          320GB
HDD RPM 	  5400rpm
HDD Interface 	  SATA

**Memory**
Memory 	          4GB
Memory Speed 	  DDR3 1066

**Optical Drive**
Optical Drive Type 	 DVD Super Multi
Optical Drive Interface  Integrated
Optical Drive Spec 	 8X DVD-Super Multi Double-Layer Drive
Read: 24X CD-ROM, 24X CD-R, 24X CD-RW, 8X DVD-ROM, 8X DVD-R, 8X DVD+R, 6X DVD-ROM DL (double-layer), 6X DVD-R DL, 6X DVD+R DL, 8X DVD-RW, 8X DVD+RW, 5X DVD-RAM
Write: 24X CD-R, 24X CD-RW, 8X DVD-R, 8X DVD+R, 6X DVD-R DL (double-layer), 6X DVD+R DL, 6X DVD-RW, 8X DVD+RW, 5X DVD-RAM

**Communications**
Modem 	        V.92 56K
LAN 	        10/100/1000Mbps
WLAN 	        Intel WiFi Link 5100 802.11 a/b/g/Draft-N Wi-Fi CERTIFIED
Ports
USB 	        3
Video Port 	1 x VGA, 1 x HDMI
Other port 	1 x Consumer Infrared (CIR) Port
Audio Ports 	Yes

**Audio**
Audio 	        3rd Generation Dolby Home Theater Audio Enhancement
                High Definition Audio Support
**Speaker** 	Two built-in stereo speakers and oneTuba                  CineBass          Booster with true 5.1 channel surround sound output

**Input Device**
Touchpad 	Yes
Keyboard 	Standard
Supplemental Drive
Card Reader 	5-in-1 card reader for optional MultiMediaCard, Secure Digital card, Memory Stick, Memory Stick PRO or xD-Picture Card
Webcam 	        Yes

**Power**
Battery 	6-Cell Lithium-Ion (4400 mAh)
Battery Life 	Up to 2.5 hours
Physical spec
Dimensions 	16.14" x 11.25" x 1.37" - 1.63"
Weight 	6.10 lbs.

It is a wonderful machine, but it runs into a few bugs that hinder it's out-of-the-box performance; namely 2 problems:
(1) all networking is impossible because of acpi
(2) the graphix card doesn't configure right and you get a "6 screens" effect

The purpose of this thread is to give all of you one place to go to get the information you need to get this laptop up and running whilst the problem is addressed. The solutions are available elsewhere in the forums, but not in one cohesive form, hence the reason I'm writing this. Lets address the first issue, networking.

**Network (WiFi and LAN)**
The existing chip sets are FANTASTIC. This really is a great machine; however, there is a bug in acpi that hinders this model's ability to network either via WiFi or via LAN. In order to do this, acpi needs to be turned off

open a terminal go to /etc/default/grub
```
 sudo gedit /etc/default/grub 
```

Look for the line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

then update grub:
```
sudo update-grub
```

then restart. This will shut off acpi and networking will work perfectly (at least it did for me). This also means that you can't monitor your battery or things like that, so if you do a lot of traveling, you'll just have to wait for the bug fixes. I, personally, am not affected cause my laptop mostly sits on a stand and stays plugged in. This should be fixed soon.

You can find the thread where I found this information by following this link:
[http://georgia.ubuntuforums.org/showthread.php?t=1305190]("http://georgia.ubuntuforums.org/showthread.php?t=1305190")

The next major problem I faced is...

:popcorn:

**Graphix Configuration**

The graphix card on this machine is VERY nice and definitely fulfills my gaming needs (yes, I have a straight Ubuntu 9.10 64-bit installation running on my system. And yes, I'm a Linux gamer. I use no other operating system currently except in virtual machines on Virtual Box). I ran into a problem when I installed the NVidia graphix driver. I thought that maybe the driver they gave me wasn't right, so I installed the NVidia drivers for my card from the NVidia website. This required shutting down the xserver and all that, but i found out that it wasn't needed from this thread:

[ http://www.nvnews.net/vbulletin/showthread.php?t=137379]("http://www.nvnews.net/vbulletin/showthread.php?t=137379")

So this is what you do. You probably have six sad little screens staring you in the face if you have just installed the drivers and they are so small that they are almost useless. just press Ctrl+Alt+F1. This will bring you to a blank screen asking you to login. It's ok if your screen is fuzzy. Login with your normal name and password. Next, in your favorite terminal-based text editor (I installed and used vim, so I'm going to give codes as if I was going through that) go to you X11 configuration file: 

```
sudo vim /etc/X11/xorg.conf
```

under the heading "Monitor" you will find a line that looks like this (however, maybe not like this cause my memory may not be COMPLETELY accurate):

```
Option "DSMP"
```

You want to change that so that it looks like this:
```
Option         "ModeValidation" "NoTotalSizeCheck"
```

then you save the file and restart your system. Your graphix card should be running in all it's beauty and glory :D.

And that should be it for the main things. Other people had problems with sound capturing and stuff, but I solved that by removing Pulseaudio. It's not quite release version and it shows. Your audio will go nuts if you leave it on there and try to play Vendetta Online or whatever else. Just, when a new version of Ubuntu is released next year, be sure to re-install ubuntu-desktop or you'll regret it. Ubuntu-desktop is removed when pulseaudio is because it's a dependency. Everything on this system runs out of the box, even the web cam (catering to my skyping needs ;)). Read on through the first thread I introduced to get the fingerprint scanner working, and enjoy your new machine :p.

---

### Post by jailbreakboy on 2009-12-11
hey have you had a problem with the DDR3 memory because it keeps reporting mine as standard DDR2, both windows and ubuntu, I can't seem to figure it out, is yours like that?

---

### Post by wagaboy on 2009-12-19
It's a great machine. But there are some issues with Ubuntu. 
I'd like to know if anyone managed to get 'multi-touch' in trackpad working. In Windows 7, multitouch works fine. Ubuntu does not recognize multitouch capability.

---

### Post by daehenoc on 2010-01-15
Hi, have you been able to get the IR device to work?  I'm just trying to find out how :)

---

### Post by bloodpuddin on 2010-04-28
Also, how did you get the mic to work?  I think I've got the sound card unleashed, but I cant get any sound input, with skype specifically.  I made sure to un-mute the mic through all sound applications, but nothing works.

---

### Post by topsugg on 2010-09-03
It's a great machine. But there are some issues with Ubuntu. 
I'd like to know if anyone managed to get 'multi-touch' in trackpad working. In Windows 7, multitouch works fine. Ubuntu does not recognize multitouch capability.

---

### Post by chingchong on 2011-01-20
I got the same laptop from newegg a while back, and couldn't be happier. There were some issues though: 
1) Camera mic didn't work pre 10.10, I read that they had updated support for camera drivers and multitouch in 10.10, so I updated. At first the mic wasn't working, the acer has a stero mic input, to fix this simply go to: Sound Preferences> Input(tab) > Connector(dropdown) select "Microphone 2". If this worked then you should see the "input level" will light up when you speak.
2) The GPU was overheating during luxrender load. To fix this I followed these links: [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)
and [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html)
and used "Nvidia X Server Settings" (gksudo /usr/bin/nvidia-settings) saved xorg.conf and added these lines:

    Option        "Coolbits" "1"
    Option        "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x2"

under Device section, this throttles allows tuning via nvidia-settings and sets the GPU to minimum to Lowest setting on battery and medium setting on AC power. Looks like this:

Section "Device"
    Identifier     "Device0"
    Option         "Coolbits" "1"
    Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240M"
EndSection

3)  multitouch pad needs tweaking, use this: [http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/)

4) When switching to the nvidia driver (recommended), you loose the auto detection of attached displays, luckily someone wrote a nice utility and script for this: [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)
see here: [http://ubuntuforums.org/showthread.php?t=1515267](http://ubuntuforums.org/showthread.php?t=1515267)

5) Cheese video recording is awful for the webcam, not sure why still searching.

Hope this helps. If your looking for a fix to the mic issue there it is!

---

### Post by chingchong on 2011-01-20
I got the same laptop from newegg a while back, and couldn't be happier. There were some issues though: 
1) Camera mic didn't work pre 10.10, I read that they had updated support for camera drivers and multitouch in 10.10, so I updated. At first the mic wasn't working, the acer has a stero mic input, to fix this simply go to: Sound Preferences> Input(tab) > Connector(dropdown) select "Microphone 2". If this worked then you should see the "input level" will light up when you speak.
2) The GPU was overheating during luxrender load. To fix this I followed these links: [http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)
and [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html)
and used "Nvidia X Server Settings" (gksudo /usr/bin/nvidia-settings) saved xorg.conf and added these lines:

    Option        "Coolbits" "1"
    Option        "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x2"

under Device section, this throttles allows tuning via nvidia-settings and sets the GPU to minimum to Lowest setting on battery and medium setting on AC power. Looks like this:

Section "Device"
    Identifier     "Device0"
    Option         "Coolbits" "1"
    Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3; PowerMizerDefaultAC=0x2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240M"
EndSection

3)  multitouch pad needs tweaking, use this: [http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/)

4) When switching to the nvidia driver (recommended), you loose the auto detection of attached displays, luckily someone wrote a nice utility and script for this: [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)
see here: [http://ubuntuforums.org/showthread.php?t=1515267](http://ubuntuforums.org/showthread.php?t=1515267)

5) Cheese video recording is awful for the webcam, not sure why still searching.

Hope this helps. If your looking for a fix to the mic issue there it is!

---

### Post by Papex on 2011-01-25
Thanks for help on the multitouch pad part! 

That actually worked! :D

---

### Post by ajit.patell on 2012-01-04
Ubuntu Blacklight fixes ACER FIXES



Create an autostartup script for Debian and Ubuntu systems


In Debian-based distributions (and here I’m also talking about the widely-spread Ubuntu), there is no rc.local file preinstalled. The good thing is that you can make one easily so you can have a place to put commands to be started up automatically at boot. Here’s what you have to do:

sudo nano /etc/init.d/local.autostart

You can name the new file whatever you want, but in this example we’ll use local.autostart. Paste
=====================================================================================================

#!/bin/sh

sudo setpci -s 00:02.0 F4.B=0


================================================================================================

CTRL+O TO WRITE FILE PRESS ENTER
CTRL TO EXIT
=======================================================

on the first line of the file and your command(s) underneath, one after the other. Now save and close and make the file executable with

sudo chmod +x /etc/init.d/local.autostart

Make the file be recognized as an init script:

sudo update-rc.d local.autostart defaults 80

Now, every time you boot up your Debian-based distribution, the commands you set in /etc/init.d/local.autostart will “magically” autostart.

---

