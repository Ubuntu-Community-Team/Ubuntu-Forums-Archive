---
title: "Ubuntu 10.4 - Intel 845 GPU - No xorg.conf"
date: 2010-06-28
forum: Hardware
---

### Post by longbeam on 2010-06-28
Hi Guys,

Im newer than new to ubuntu and am having real trouble with graphics drivers.

I downloaded Ubuntu 10.4, burned it to CD and installed on my old Dell Inspiron 1100 laptop, along side XP.

On first boot I ended up at a black screen but heard bongo's going in the background. Just a graphics driver I though - rebooted back to XP to search the net.

Found a forum post saying to key CTRL ALT F1 to get to a terminal and then run the command:

sudo dpkg-reconfigure xserver-xorg

So this I tried. Ubuntu booted to a GUI and I thought I was set, but no. Not this time. My screen was stuck in 640x480 and there were no displays listed in system - preferences - monitors.

Since then (2days ago) I have reinstalled and done a shed-load more searching to find that I have no xorg.conf. At all. The only thing I have is a xorg.conf.failsafe which im guessing was created by me using the 'failsafe x' mode from recovery options in GRUB.

I was/still am disappointed that Ubuntu cant even manage a GUI on first boot but instead of snapping the CD and formatting the partition back to NTFS I have made my own xorg.conf file using a few bits I have found on the net. I can now boot to a GUI but only after a warning about no i810 driver and only in failsafe x mode. I do now have a display listed in system - preferences - monitors but am unable to change any settings at all, im still stuck in 640-480.

So far my xorg.conf looks like this:

Section "Device"
Identifier "Intel 845"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 64000
Option "UseFBDev" "false"
EndSection 

Section "Screen"
Identifier "Default Screen"
Device "Intel 845"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768_75" "800x600" "640x480"
EndSubSection
EndSection

Any ideas on how to sort this out? Any help would be much appreciated!

---

### Post by oldfred on 2010-06-28
I have nvidia so I do not know if this applies to your model or not:

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

