---
title: "[SOLVED] need help: Matrox TripleHead2Go in Ubuntu 7.10"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by gfixler on 2007-11-21
I've just built a great new system with all new parts from Newegg. After an unfortunately arduous setup, with endless problems spelled out in a tale of woe [here on Flickr]("http://www.flickr.com/photos/garyfixler/2046569457/in/set-72157603238442195/"), I got everything installed, and switched from the 17" monitor to the Matrox TripleHead2Go, itself plugged into 3 19" Dells. It just worked, and perfectly! [Here's proof!]("http://www.flickr.com/photos/garyfixler/2046570507/in/set-72157603238442195/")

That's a fresh install of Gutsy on a brand new custom box, spread over 3 screens! It worked fantastically for 7 full hours, stable as could be, as I tested out everything from Flash in Firefox to every last feature of Compiz Fusion, which looked amazing on 3 screens (biggest cube I've ever seen!). I even got Wine+Steam+Portal installed, and working almost perfectly, save for the textures being all crazy colors. It was fast, super smooth, and rock solid. I went to bed.

The next day, after work, I booted up, and nothing - black screen after the BIOS. At some point, even the BIOS wouldn't show up for me anymore. I tweaked for 2 hours, and ultimately tried an analog VGA cable w/ DVI adapter from the 8800GTS, straight to 1 Dell 19". That worked. It had been booting every time, but not displaying.

Tonight - night 2 of trying to fight this - I found [this]("http://www.openscenegraph.org/index.php?page=KnowledgeBase.TripleHead2Go"), and tried everything from making a custom xorg.conf based on it, to flat-out pasting all the display-based stuff straight over my xorg.conf file. I even let nvidia-settings blitz it all in favor of a new one - which worked for one display fine - and then just added in enough to get that guy's modelines in there, yet it didn't work through the TH2G. Black screens again.

I know it can work. It worked fantastically for 7 hours. I need to track this down. I've pinned a lot of hopes on this, and have spent quite a bit (new monitor, Ergotron LX arm, 8800GTS, and days of my free time troubleshooting). I can still get in through analog VGA. I have yet to test straight DVI to a single monitor again, though I imagine it will work. Everything else is just great.

What do I do next? What info can help anyone here to put me on the right path? I've backed up dated versions of each xorg.conf file as I tried it. None of them has shown anything after the BIOS but black, but I can upload them here, if necessary. Are there diagnostics? Error files? Something I can read up on? I didn't understand that modeline calculator in the link I found, but it actually saw me reading up on back porch, front porch, breezeway, horizontal and vertical sync pulses, and a bit more. I didn't want to become an expert on this kind of stuff just to get 3 screens working (again) :) Any help would be great. Thanks!

---

### Post by gfixler on 2007-11-23
A development has occurred.

If I boot into recovery mode from GRUB, I get tossed eventually to a root prompt. If I kill out of there - e.g. w/ Ctrl+d - it dumps me to the graphical login, which nicely spans the 3 monitors! I can log in as usual, and everything works fantastically, as it did in the mentioned initial 7 hours of joy.

I had a friend consider that it might be the USB power to the TripleHead2Go box, which gets power through a USB cable from the PC, so tonight I borrowed a charger adapter that plugs into the wall, and has a USB port on the bottom, and plugged the TH2G into that. Not only did that not work, but the leftmost monitor seemed not to want to come up at all. Maybe the charger wall-wart adapter was a bit underpowered. It still wouldn't properly boot, either. Black screen forever until reboot. I changed it back to PC-power.

Any clues now? Apparently the only problem I've really ever had on this machine this past week was signal not getting through the DVI cables. Even one monitor doesn't like to boot properly through DVI, but any will boot fine through a single VGA connection, and single, or triple screens work if I go the recovery mode w/ ctrl+d at the root prompt route.

Thanks for any advice.

---

### Post by clubsoda on 2007-11-27
I doubt I can help but this looks like a whole lotta fun.  Correct me if I'm wrong, but the TripleHead2Go doesn't require any drivers, right?  It must interrogate the screens for their dimensions, then pretend to be a single screen with the combined total width and a suitable height(?)
I'm assuming you have the restricted nVidia driver installed for your graphic card.  My only suggestion would be to have a good look at /var/log/Xorg.0.log for any hints as to what might be going wrong.
Also, since your graphic card is already capable of driving multiple screens, is it possible that it sees the huge screen size setting and divides that automatically between its own outputs?  Pure speculation on my part, but maybe that's why the first screen is not showing.

---

### Post by gfixler on 2007-11-28
Right, no drivers. It does come with a utility that sits in the Windows shelf, and will allow maximization to the current monitor (or all with ctrl). The TH2G does reveal itself to the PC as a single, giant monitor, and then breaks up the signal to the three actual displays.

I do have the restricted nVidia driver. I had a peek at Xorg.0.log, but can't make much out of it. Should I post it for everyone to peruse? I don't really know what to look for, or what any of it really means.

I don't think the card is having trouble, as it won't even work through a DVI hookup to a single monitor, with the TH2G completely out of the picture. It will show through an analog VGA hookup, but even just the 1 DVI plug + 1 monitor, I have to get in through the back way (recovery mode, then kill out of the root prompt), so it's not really a TH2G problem after all. It's something about the card, or the regular bootup procedure not letting a DVI signal through.

---

### Post by kevinfishburne on 2007-12-03
I had the same problem. It worked for a while through the DVI output (using the DVI out on my video card and VGA2DVI adapters for my 3 21" CRT's), then it just quit and showed a red light on the TripleHead2Go.

The solution (knock on wood, I just got it working) was to connect both the DVI and VGA output on my video card to the TripleHead2Go at the same time, then use the nVidia settings manager to detect the displays after power-cycling the TripleHead2Go (unplugging the USB cable). I then chose to disable the VGA display in the nVidia settings manager, but left it connected for good measure. I suppose using TwinView would work as well... Hopefully things will stay this way, because Open Arena and Nexuiz are absolutely insane with an 180 degree view radius.

Kevin

---

### Post by gfixler on 2007-12-30
Thankfully a Google Alert for my name brought up this page again so I could mark it solved, and explain how, as I solved it a few weeks back.

The thing causing the black screen was the "splash" option in the kernel line of the grub menu.list. Just delete the word "splash" entirely from the command arguments in that file for the default boot choice, and reboot. I've since found that error solved in other places here, and elsewhere. I don't quite recall what it was, but it came down to a bug in the splash screen with DVI, somehow.

---

### Post by gfixler on 2008-02-09
I was asked offsite to post the xorg.conf file I use to get my 3-screen desktop working with the Matrox TripleHead2Go Digital Edition, so here goes - this is what I have currently, and it works great:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

Also of note - I've had to go into my /boot/grub/menu.lst, and delete the word "splash" from the 'kernel' line. This tries to use a splash screen during startup, but throws the whole machine into blackness from just after the BIOS startup screen onward. At that point, the only way out of it is to boot into recovery mode, and when dumped to the shell, either type 'exit' or hit ctrl+d to kill out of the shell, which will do some quick exit routine, and dump you at the graphical login shell, where you can log in. If you just remove "splash" from that file, however, it'll dump you automatically to the graphical login. This needs to be fixed after certain kernel updates, which fix the menu.lst, and re-add the "splash" word back in. Good luck.

---

