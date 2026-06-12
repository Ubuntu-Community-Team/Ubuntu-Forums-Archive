---
title: "Cyberblade/XP resolution/video out problems"
date: 2009-01-27
forum: Hardware
---

### Post by orangeisorange on 2009-01-27
**EDIT:** Fixed my resolution, the xorg.conf below worked out for me suddenly when I booted today, even though I don't think it did when I rebooted yesterday.  So I just need video out help

I would like to be able to use TV out function (I have made no headway in this, I don't even know where to start).  I'm rather new at this, so being as explicit as possible would be helpful, although I've gathered that commands generally get typed into "Terminal."

Attempts to find the graphics driver or update it have proven fruitless.  System>Administration>Hardware Drivers tells me I have no proprietary drivers in use.  I am using Ubuntu 8.10.  For what it's worth, I am trying to use Ubuntu on a very old laptop (circa 2000) with a Cyberblade/XP graphics card from Trident Microsystems.  

I edited my xorg.conf to the specifications of [this thread]("http://ubuntuforums.org/showthread.php?t=763964&highlight=cyberblade&page=5") with [s]no[/s] success.  Here is my current xorg.conf:

Section "Device"
Identifier "Trident Microsystems CyberBladeXP"
Driver "trident"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
Option "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Generic Monitor"
Device "Trident Microsystems CyberBladeXP"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768_60.00" "800x600"
EndSubSection
EndSection

Thanks for your help in advance.

---

### Post by orangeisorange on 2009-01-31
I have made some progress.  I was able to get the VGA out working, I think doing [this]("http://ubuntuforums.org/showpost.php?p=4553231&postcount=15") was what did it:

1. sudo nano /etc/initramfs-tools/modules
and add

fbcon
vesafb
tridentfb

2. sudo update-initramfs -u

3. sudo nano /etc/modprobe.d/blacklist-framebuffer

in lines vesafb and tridentfb set a # at the beginning

4. Reboot

Then I used Fn-F5 to switch between LCD, TV, and LCD/TV and everything worked great, visually.

Initially I had perfect video but no audio, but I fixed this by going into my settings on the tv and switching "pc audio" from "no" to "yes."  (Thanks dad for that suggestion lol.)

So, in a sense/tecnically, my problem is solved, except I still don't know how to use the TV-Out function with the composite cable, and I would prefer to use it for ease of plugging/unplugging and compatibility with televisions that may not support VGA.  I believe I've found the CyberbladeXP [driver manual]("http://www.xfree86.org/4.7.0/trident.4.html#sect4"), and I suspect I need to tweak either "TVChipset" or "TVSignal" but I'm not sure and wouldn't know what to do even if I was sure.

---

