---
title: "Screen Resolution - Not picking up xorg.conf settings after restarting x"
date: 2008-06-11
forum: Hardware
---

### Post by dea_jul on 2008-06-11
Hey there,

I just installed kubuntu on a new system, but I'm having trouble getting KDE to recognize the proper screen resolution. I know this is a fairly common problem, but I've exhausted the resources I've been able to find with no luck. 

For starters, I'm using an IBM thinkvision monitor on kubuntu 8. The screen resolution should be 1280x1024, but after a clean install, it is set to 640x480 (which, when expanded to the screen, makes the desktop environment nearly unusable). 

I tried opening krandrtray from the system apps menu, but it seems to crash on opening. Running it from the terminal results in nothing helpful: 
```
juldea@k-desktop:~$ krandrtray
juldea@k-desktop:~$ sudo su
[sudo] password for juldea:
root@k-desktop:/home/juldea# krandrtray
kbuildsycoca running...
Reusing existing ksycoca
juldea@k-desktop:~$
```
Previously, I was able to get it to print out a message that it wasn't able to interface with randr, possibly because it had crashed, but I'm unable to duplicate that message now. 

So, I manually checked xrandr: 
```
juldea@k-desktop:~$ xrandr -q
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0*
   320x240        51.0
juldea@k-desktop:~$
```

Seeing the proper resolution wasn't available, I tried editing my xorg.conf file to include it. I changed the screen section to reflect the following (The subsection is the addition and only change):
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth          24
                Modes         "1280x1024"  "1024x768"  "640x480"
                Virtual       1280 1024
        EndSubSection
EndSection
```

I restarted X, which resulted in *entirely* unreadable text in terminal and on menus (the same resolution is fine on windows), but strangely, with no change at all to the taskbar, panels, konqueror, etc. I can post a screenshot, if necessary.

I set the resolution manually with xrandr, hoping that maybe it would pick it up that way, but to no avail:
```
juldea@k-desktop:~$ xrandr -s 1280x1024
```


I started getting frustrated at that point, so after googling, I tried a number of other suggestions, including reconfiguring x with dpkg:
```
juldea@k-desktop:~$ dpkg-reconfigure xserver-xorg
```
...And rebooting (which resulted in an unusable xorg.conf file - forcing me to restore from the backup [?]), as well as installing kcontrol in hopes of being able to set it there. Unfortunately, my install of kcontrol has no option to change the screen resolution. I've looked in every panel, and I've used its built in search function. "Resolution" turns up no results, and "screen" turns up "screensaver" and "screen saver". 

I've also tried uninstalling and reinstalling my restricted nvidia drivers, but to no avail (without them, I can't start x, and after a reinstall I encounter the same problem). 

If I go to "System Settings" > "Display", I am able to select a resolution for the monitor, but I am limited to 640x480 and 320x240, along with the current resolution stored in my xorg.conf file. Even with the current resolution (apparently) active for half the system (terminal, menus, etc), the display section shows 640x480 as the current. And, if I try to change it to (what should be) the current setting, I get a screen which is hugely out of bounds of my monitor, and which is still ridiculously bloated. I'm really at a loss...

Any help would be greatly appreciated. Even just pointing me in the right direction would be awesome. I'm very happy with how everything looks and functions so far, but without a resolution at least closer to the actual value, the system is (unfortunately) unusable. 

Thanks a lot,
Jules

I doubt this is useful, but the output of lspci is:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01)
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
```
I can post lshw, or any other info, if desired. 

Thanks!

---

### Post by shak541 on 2008-06-11
first thing check in your etc/x11/xorg.conf file to see if the driver is correct. Secondly try removing all display modes you do not want showing( this worked for me with a 1280 by 800 resolution monitor. If x doesn't start after this use nano to edit your xorg file back. Hope this works out for you :D

---

### Post by dea_jul on 2008-06-13
Thank you again for the response! I had actually tried out your suggestions previously (and I gave them another shot after reading your reply), but taking the time to help me out is really appreciated anyway! 

I spent the whole day screwing around with settings (literally, the whole day) to try to get this thing to work, to no avail. Finally, 3 minutes to midnight, I tried one, last, configuration I had found on google, made a few modifications here and there, and reluctantly restarted X before quitting for good. I was absolutely *stunned* to see that it actually worked. 

Again, I really appreciate you taking the time to respond to my post (especially since so few others did). While your answer didn't directly lead me to the problem, the effort is truly appreciated nonetheless. 

For others, here is the proper xorg.conf file I was able to generate. (It's nothing spectacular, but for some reason I wasn't able to get **anything** else to work for me, including installing nvidia drivers, running their tools, grabbing other configurations, manually creating them from scratch, even generating and inserting every modeline and mode I could find into the freaking config file, and so on). So, for anyone with an IBM thinkvision, this is for you. 

Thanks again.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
  Identifier    "l201p"
  DisplaySize   400 300
  HorizSync     30-80
  ModelName     "l201p"
  Option        "DPMS"
  VendorName    "IBM"
  VertRefresh   55-85
  Modeline      "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066
EndSection

Section "Screen"
        Identifier      "external screen"
        Device          "i910GML"
        Monitor         "l201p"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "external screen"
EndSection

---

