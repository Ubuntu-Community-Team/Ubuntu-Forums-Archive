---
title: "New NVIDIA Geforce FX 5200 video card not working properly"
date: 2009-03-07
forum: Hardware
---

### Post by urlacher3292 on 2009-03-07
I recently purchased a new video card (made by Chaintech), so that I could finally upgrade from Hardy to Intrepid. My onboard card is a now unsupported Intel 82845. The old Intel works after an update, but Compiz cannot be used.

After booting into Intrepid and installing the NVIDIA drivers i reboot using the video card, but the screen goes blank. I have tried for two days to install the drivers, but the graphics card just will not work. I have tried the 177, 173 and 96 drivers. None of these allow the computer to boot properly. I can't even use a Live CD with the new graphics card because startup freezes. Any help getting the new card, or even my old integrated chip to work would be greatly appreciated.If any files need to be posted or tech. info given please just ask.
By the way, the new card installed and works flawlessly under Windows XP.

---

### Post by taurus on 2009-03-07
How did you install the driver(s) for your nvidia graphic card?  Did you install it from System -> Administration -> Hardware Drivers?  You need to install the 173 (legacy one) driver, not anything newer.

---

### Post by urlacher3292 on 2009-03-08
Thanks, I will try the legacy drivers again. Is there anything that seems obvious that I should do? I haven't been using ubuntu for very long.

Edit: I got the NVIDIA drivers working by editing my xorg.conf file, but I cannot get visual effects to work they're the only reason that I bought the card. Is this related to my onboard chip which also will not run the visual effects and if so can I fix it?

---

### Post by PCMben on 2009-03-12
I also have a problem with the same graphics card. Using the "Hardware Drivers" utility (Ubuntu 8.10), I can get the graphics card sort of working with the 173 driver. The first few times, I had a similar problem with the screen going blank. I then booted up through the recovery mode and then went to the option of "xfix" and tried a few more times of installing through the "Hardware Drivers" utility. Eventually, it started to sort of work, as per below.

I am trying to get mine working with dual screen. One LCD screen is plugged into a VGA to DVI adaptor then into DVI port. The other LCD screen is plugged through a KVM switch (to use this monitor with two computers) which is then plugged into the VGA port. 
A number of things can then happen:

1) The monitor through the KVM switch boots up ok, but the Xserver does not work, and the Compiz things do not work, but there are many selectable resolutions to choose from. The second monitor through the VGA to DVI adaptor then shows flashing colours.

2) Other times, the Xserver works, with the monitor through the VGA to DVI adaptor working ok with selectable resoultions and Compiz working. However, the second monitor through the KVM switch is seen as a CRT, and there are only two very low resolutions which are selectable. These low resolutions do not work well.

So, all I can suggest is trying the xfix and reactivating the 173 driver a few more times and see if it works. Maybe try downloading and installing EnvyNG and installing the 173 driver through that (I tried that a few times), but maybe that is the same as installing the driver through the "Hardware Drivers"?

If anyone has any ideas on how I can get my dual screen working better, that would be very much appreciated.

---

### Post by bigbudz on 2009-05-31
Can anyone get the nvidia GeForce FX 5200 working with a DVI cable? 

Is there a problem with the nvidia 173 driver and DVI output?

Ive read so many posts about this but no answer yet. When I use the DVI cable the max resolution is 1280x1024 which is stretched across my native screen res of 1920x1080. I have tried; 

1. Using the VGA cable. This works fine, outputs in native resolution by itself.(This threw off the res on my second display, its 4:3 but outputs 1024x768 with small black bars on top and bottom giving a aspect ratio of about 1.45) I'd really like to get DVI working. 

2. Editing xorg.conf. I tried adding the modeline i want but nothing. I tried changing CRT to DFP, still nothing. Does linux think my DFP is a CRT? Don't know what else to try. Heres my edited xorg.conf
--------------------------------------------------------------------
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2343"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
	Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
	Modes		"1920x1080"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "TV: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
------------------------------------------------------------------------

Any input would ultra appreciated...

---

