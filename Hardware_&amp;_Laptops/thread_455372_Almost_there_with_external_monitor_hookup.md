---
title: "Almost there with external monitor hookup"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by dada12 on 2007-05-26
Hello, 

I just installed Ubuntu Studio.  Its been seven years or so since I've played with Linux.  Glad to be back though!

This is my trouble:

I have  Dell XPS1210 laptop and an external LCD monitor which I prefer to work on at home.  I am trying to force Ubuntu to use the external monitor only.

I installed nvidia-settings, but the TwinView is grayed out under "Display Device"

I edited the xorg.conf file and now the ONLY video I get is through the external monitor, it look amazing, but I don't get anything  on my laptop screen.  I would like to be able to only use my external monitor at home, but obviously, when not plugged in, the laptop's screen should work.

Here is my xorg file, I just can't figure out where I messed up in the config...

Section "Device"
    Identifier     "nVidia Corporation G72M [GeForce Go 7400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "ConnectedMonitor" "crt"
    Option         "TwinView" "1"
    Option         "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 		   1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
    Option         "SecondMonitorHorizSync" "31-81"
    Option         "SecondMonitorVertRefresh" "56-75"
	#Option "NoPowerConnectorCheck"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"

		#Viewport 0 0
        Depth       16
        Modes      "1280x800" "1280x1024"
    EndSubSection
    SubSection     "Display"

		#Viewport 0 0
        Depth       24
        Modes      "1280x800" "1280x1024"
    EndSubSection
EndSection

========================

Could "ConnectedMonitor" force the signal only to the external LCD?

Thanks so much for your help, if I can get this figured out, I am immediately porting all my music projects to Ubuntu Studio!!

Arto

---

