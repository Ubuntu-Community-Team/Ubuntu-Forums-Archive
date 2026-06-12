---
title: "Hibernate/Standby doesn't work! Help."
date: 2008-11-26
forum: Hardware
---

### Post by Fizzdan on 2008-11-26
Hi all,

I am new to mythbuntu. After installing 8.10, updating packages and activating the nvidia driver 173 and playing with it for a while, it seems to be going well apart from the Quit methods.

First; I don't know if this is related to the hibernate/standby issues or not, but selecting restart from the quit menu brings up the login window instead of just restarting the system as expected. Whereas shutdown does indeed run the shutdown sequence but fails to power down the system leaving the fans and power led on until the power switch is pressed.

Hibernate experience:
Selecting hibernate causes the screen to go black with a flashing cursor in the top left corner while the hdd led flashes writing the file, finally the monitor goes into standby and the hdd stop spinning. But like the shutdown above it leaves the fans running and the power led on until the power switch is pressed. Restore in the splash screen is see "Waking up. Please wait" after a few seconds the progress bar freezes. Nothing seems to help but a reboot.

Suspend experience:
This seems to be complete very fast putting the monitor into standby and spinning down the hdd but yet again it leaves the fans running and the power led on until the power switch is pressed. Restore there seems to be no way to get it to wake, the power switch, keyboard, mouse etc.. does nothing, only pressing the reset switch seems to work.

So obviously there is something I need to configure, however I have been unable to find anything 8.10 specific in the forums.

For the record hibernate and standby work perfectly on this system when running winXP, so the hardware seems capable.

Thanks.

System details:
lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0a.0 Ethernet controller: Standard Microsystems Corp [SMC] 83c170 EPIC/100 Fast Ethernet Adapter (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

/etc/X11/xorg.conf
Section "Monitor"
        Identifier     "ViewSonic E70"
        HorizSync       31.5 - 57.0
        VertRefresh     50.0 - 70.0
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Device         "nvidia FX5200"
        Monitor        "ViewSonic E70"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
                Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x576" "800x600" "640x480"
        EndSubSection
EndSection

Section "Module"
        Load           "glx"
EndSection

Section "Device"
        Identifier     "nvidia FX5200"
        Option         "DPI" "100x100"
        Option         "UseEvents" "1"
        Option         "AddARGBVisuals" "1"
        Option         "AddARGBGLXVisuals" "1"
        Option          "ConnectedMonitor"      "CRT"
        Option         "TVOutFormat" "COMPOSITE"
        Option         "TVStandard" "PAL-B"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

---

### Post by razy60 on 2008-11-27
This is probably not much help as I'm a noob at this but, i had a similar problem which turned out to be the fact that i did not have enough swap allocated.

Raz

---

### Post by ZanexGt on 2008-11-27
I just upgraded to Intrepid after using Gutsy on my Compaq F730US for over a year. After the upgrade, Suspend no longer worked. I ended up installing the nVidia Restricted Drivers and that completely fixed the 'Suspend' behavior of the laptop. 

I'm not sure if you are running ATI/nVidia/other but it's worth a try to install the proprietary drivers for your laptop. 

The problem with mine was that the standard Intrepid default video driver wouldn't reinitialize the screen after Suspending. Good luck!

---

### Post by Fizzdan on 2008-11-27
Thanks for your suggestions but, no it's shouldn't be swap as I have plenty and I am running with the restricted drivers activated already.

free -m
             total       used       free     shared    buffers     cached
Mem:           755        517        238          0         16        227
-/+ buffers/cache:        273        482
Swap:          972          0        972

Anyone else know what I need to do to get it working?

---

