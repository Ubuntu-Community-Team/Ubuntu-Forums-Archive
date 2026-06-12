---
title: "NVidia Performance Issue"
date: 2010-08-08
forum: Hardware
---

### Post by nickdbarron on 2010-08-08
It's been a long time since I've posted (so long in-fact, I don't remember my username). I have just installed Ubuntu onto my laptop and everything works great. I do, however, have an issue with gaming on this laptop. It seems like performance of my video card is down a bit (as opposed to the Window 7 install formerly on this machine). I don't know much about Linux, I've dabbled here and there, and would like to know if there is a fix for this. I have searched forums and ran a few of the tweaks, but nothing seemed to work.

Laptop: Dell XPS m1530
Video Card: GeForce 8600m GT
Linux Version: 10.4

Steps tested so far:

I have installed the NVidia Current (recommended) from the Hardware Manager.

I disabled the PowerMizer settings in the NVidia X Server Settings Utility - no results +- (It is now re-enabled and the power setting is 2)

I created the nvidia-power.sh file with the following:
[I]#!/bin/bash

while true; do
if on_ac_power; then
nice /usr/bin/nvidia-settings -q all > /dev/null
fi
sleep 25;
done
[/I]

I also ran sudo gedit /etc/X11/xorg.conf with the following:
[I]Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection[/I]


Other Terminal commands: 
sudo dpkg-reconfigure xserver-xorg - No effect +-

I have rebooted the machine between each step and when I run the System Testing Utility and there doesn't seem to be a problem. Now, I know my video card isn't that great and the performance difference between Ubuntu/Windows isn't 'off' by a lot - I just simply would like it to function fully.

Game used to test functionality: 
World of Warcraft 9-40 fps
Unreal Tournament 80-120 fps

Please, if there is a pro out there, be my guide. :)

Regards

NickDBarron

---

### Post by Fafler on 2010-08-09
If OpenGL works properly, your problems probably lies somewhere else. First, test OpenGL with a native Linux game. I use Doom 3 for that. If it works okay, the problem is in the Wine/WoW configuration. Theres several guides out there about optimizing performance. Look at winehq.org.

---

### Post by nickdbarron on 2010-08-09
I will research this further today and test it. Thank for pointing me in a direction. I have ut2k4 installed and it seems to run fine. I will be going to work, so my results will not be posted for at least 12+ hours of this post. Again, thank you.

---

### Post by nickdbarron on 2010-08-11
UPDATE:

Thanks for your patience. I did some further research and Ubuntu 10.4 only appears to have a NVidia repository up to 190.x.x. I downloaded the newest drivers from NVidia's website and saved it to my home directory. I'll post my step by step. This information isn't original, but extrapolated rather.

1. Add items to Blacklist file. I am not sure what these items are, honestly. I can only assume they are used to 'auto-find' certain driver sets.
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add the following at the end of the file and save it:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

2. Uninstall all known NVidia drivers using terminal
```
sudo apt-get purge nvidia*
```3. Reboot PC. At this point, you will have no GUI, Ubuntu will not load. It will produce an error and give you options. Select the 'Exit to Terminal' option.

4. Log in using your credentials. Now run the installer of the NVIDIA file you copied to your Home directory.
```
sudo sh NV
```- All you need to type is what is there and press TAB, this will auto-fill the filename. Press ENTER after the line is complete.
- Go through the 'wizard'. I didn't see any walk-through on this, but it is pretty self explanatory.

5. Restart the GUI/GDM
```
sudo service gdm start
```Now, I have the newest driver installed, even though I am not entire sure that solved the issues. I will need to test it, but I am now at work. :(

Steps taken from following sites:

[HTML]http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04
http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html[/HTML]

---

### Post by nickdbarron on 2010-08-13
Update: This did help my video card performance, slightly. At least I am confident the current driver is in use.

I will consider this closed, unless other gurus have advice.

---

