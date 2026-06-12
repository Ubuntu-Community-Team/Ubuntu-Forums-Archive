---
title: "Complex GUI problems after 9.04 upgrade"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by pendlaren on 2009-06-25
Folks,

After upgrading from 8.10 I have experienced some trouble with my GUI. I don't know what is related or not:

1. On boot, I expect the default black background with the Ubuntu logo in the lower right, which I know as the Jaunty login screen. But quite often I get an error message saying "Failed to open file '/usr/share/gdm/themes/HumanCircle/../Human/ubuntu.png': No such file or directory" (which I support, because I can't find that file neither, only /usr/share/gdm/themes/HumanList/ubuntu.png). Instead I get a login screen with blue background and a yellow flower in the lower right corner.

2. Problem is, usually, that there are no mouse click reaction. I may log in by entering username <ENTER> and password <ENTER> but then I can't click anything. Neither does Ctrl-Alt-Backspace work, but Ctrl-Alt-F1 does, and I can run /etc/init.d/gdm restart, which sometimes takes me to the black login screen, and sometimes the blue, but almost always the mouse button click works after one gdm restart.

3. When logging in, even if the mouse button is working, I am not able to drag the mouse pointer further right on my left screen than about 20% from the right edge of the screen. When dragging a window, I can move that so far to the right that the left border of the window is 20% from the edge, but the mouse pointer is released after this drag-and-drop operation, and I can drag it over to the right (internal) monitor. The solution I've found is to open the gnome-display-properties, swap placement of the monitors, press Apply and then "Restore Previous Configuration". Then I can drag windows over to the other screen, and everything is OK.

4. From time to time, the GUI seems to hang for some seconds (approx 5-30) even though no prosesses are using a lot of CPU. I can move my mouse, which automatically gives focus to windows I move over, but no input seems to have any effect. E.g. I may press Enter many times in a gnome-terminal, but nothing happens. I am able to Ctrl-Alt-F1 over to text console and run top or anything else, but the Gnome session is hanging until it suddenly catches up, and all my keypresses and mouse clicks have obviously been recorded, and are kind of played now, e.g. gnome-terminal shows lots of prompts.

The latter may be related to an application, I guess, but the three first points seems Gnome-related and very strange to me.

My spec:
IBM Lenovo T60 laptop with 3GB RAM and ATI Technologies Inc Radeon Mobility X1400 graphics card, running dual screen.

I may add that I've run Ubunutu since 7.10, upgraded twice a year with no big problems. With Live CD I was actually able to run some visual effects, but not on HD installation.

Here are the device section of my xorg.conf, if it helps:
```
Section "Device"
        Identifier  "Generic Video Card"
        Driver  "ati"
        Option      "DesktopSetup" "horizontal, reverse"
        Option      "no_accel" "no"
        Option      "no_dri" "no"
        Option      "MonitorLayout" "LVDS, CRT1" #"LVDS, NONE" #"AUTO, NONE" #"LVDS, AUTO"
        Option      "CRT1Position" "LeftOf"
        Option      "MergedFB" "true"
        Option      "IgnoreEDID" "off"
        Option      "Mode2" "1680x1050"
        Option      "HSync2" "unspecified" #"31.5 - 90.0"
        Option      "VRefresh2" "unspecified" #"75"
        Option      "ScreenOverlap" "0"
        Option      "NoTV" "yes"
        Option      "TVStandard" "NTSC-M"
        Option      "TVHSizeAdj" "0"
        Option      "TVVSizeAdj" "0"
        Option      "TVHPosAdj" "0"
        Option      "TVVPosAdj" "0"
        Option      "TVHStartAdj" "0"
        Option      "TVColorAdj" "0"
        Option      "GammaCorrectionI" "0x00000000"
        Option      "GammaCorrectionII" "0x00000000"
        Option      "Capabilities" "0x00000000"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "CenterMode" "off"
        Option      "PseudoColorVisuals" "off"
        Option      "Stereo" "off"
        Option      "StereoSyncEnable" "1"
        Option      "FSAAEnable" "no"
        Option      "FSAAScale" "1"
        Option      "FSAADisableGamma" "no"
        Option      "FSAACustomizeMSPos" "no"
        Option      "FSAAMSPosX0" "0.000000"
        Option      "FSAAMSPosY0" "0.000000"
        Option      "FSAAMSPosX1" "0.000000"
        Option      "FSAAMSPosY1" "0.000000"
        Option      "FSAAMSPosX2" "0.000000"
        Option      "FSAAMSPosY2" "0.000000"
        Option      "FSAAMSPosX3" "0.000000"
        Option      "FSAAMSPosY3" "0.000000"
        Option      "FSAAMSPosX4" "0.000000"
        Option      "FSAAMSPosY4" "0.000000"
        Option      "FSAAMSPosX5" "0.000000"
        Option      "FSAAMSPosY5" "0.000000"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "UseInternalAGPGART" "yes"
        Option      "ForceGenericCPU" "no"
        BusID       "PCI:1:0:0"
EndSection

```
regards,

---

### Post by moster on 2009-06-25
buddy, if I were you, I would run clean Jaunty installation. Who knows what happend...

---

### Post by pendlaren on 2009-06-30
> **moster said:**
> buddy, if I were you, I would run clean Jaunty installation. Who knows what happend...

Thanks, I thought that was the Windows approach, and hoped for a "cleanup" solution :)

---

### Post by moster on 2009-06-30
It is more of general software imperfection. :)

Problems would be near zero if you installed 8.10 version and then right after that 9.4. But if you install 8.10 and then ton of software and you change much of system to suit you, and then upgrade to 9.4 then you have more possibility for mixup.

You mention windows... well, in windows is all that much worse because use of registry and already in system is so many GB of crap that slow begin to crawl with time.

I personally do not have problems changing linux every 6 months because I changed WinXP every 2 months. And last few weeks of that 2 month was OS already garbled. Vista is better for that particular but she has some other problems that I cannot now mention because this post would be 2 pages long :)

edit:
You have generally problems with GUI/VGA. It can be because ATI drop support for your graphic card. It is stuck at 9.3 version. New X in jaunty cannot work with old proprietary vga drivers you already had from previous version...  I am just guessing, I think only God know why is happenig what is happening :D

---

