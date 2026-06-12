---
title: "Dell Inspiron 600m Freezes after 9.10 installation"
date: 2010-01-02
forum: Hardware
---

### Post by 98cwitr on 2010-01-02
Tried to run updates (Update Manager), locks up, tried to open firefox and it locks up. Also, tried to run *sudo apt-get install update* and it could not find update package...could not find upgrade nor any other repos for that matter. Anyone got an idea of wtf is wrong?

---

### Post by 98cwitr on 2010-01-03
DOES NOT happen in 9.04. Using it right now. All updates are installed and the system is running fine (for what it is).

---

### Post by 98cwitr on 2010-01-08
anybody? Would love to upgrade :)

---

### Post by Don Bowen on 2010-01-17
I'm having the identical problem with same machine.
9.10 installs fine, boots, and runs....but if you try to run any program after that...
it hangs so badly you have to hold the power button down to reboot.
Anyone else have this problem?  Anyone solve it?

---

### Post by bof83 on 2010-01-19
I'm having the same problem and I just found out that the problem is documented here:

[http://ubuntuforums.org/showthread.php?t=1305349&highlight=radeon+drm+agp+freezing](http://ubuntuforums.org/showthread.php?t=1305349&highlight=radeon+drm+agp+freezing)

it seems like there is a problem with the driver x11 uses, so you can either switch it or use the proprietary one...

---

### Post by bof83 on 2010-01-19
This is the final /etc/X11/xorg.conf I ended up using:

Section "Device"
        Identifier "ATI Radeon"
        Driver  "ati"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AccelDFS" "false"
        Option "EnablePageFlip" "true"
        Option "EnableDepthMoves" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon"
        DefaultDepth    24
EndSection



I had to disable AccelDFS; I had graphics flickering and corruption problems otherwise.

---

### Post by vortmax on 2010-01-19
Do you have one of the legacy ATI cards that they dropped driver support for?

I have an Inspiron 6000 with an ATI x300 card running kubuntu karmic.  I was having an issue where it would boot and let work, but if too many dialogs opened up at once, X would lag and freeze.  It seems to happen more at high system loads.  Turning off composting seems to have fixed it.

I tried enabling the backports and upgrading to the most recent version of KDE, but it almost seems worse.  It could be though that I had strigi running with the old redmond engine which was killing the CPU.  I haven't experimented since taming that down.

---

### Post by bof83 on 2010-01-21
Yes, I turned of compviz and it seems to work even with AccelDFS turned on. (compviz is disabled in gnome by going to System->Preferences->Visual Effects and setting it to None)
 thanks

---

### Post by cruelwill on 2010-01-21
i am using ubuntu 9.10. i am having serious problem with linux Dc. when i  trt to open it ,the window appears for a moment and closes automatically .please help[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

