---
title: "Problems with X server on Acer Travelmate 4001"
date: 2008-12-02
forum: Hardware
---

### Post by teranex on 2008-12-02
Hi,

I just installed Ubuntu 8.10 on an Acer Travelmate 4001WLMi using Netboot (the DVD-drive is broken :( )

Installation went fine, and i could login to my freshly installed ubuntu. However after i logged in for the first time i saw the desktop with all the panels, but then the only think i could do was move my mouse, no clicking or typing anymore...

After some browsing on the forum and google i found it to be a problem with my x-server. After running one of the commands from [this thread]("http://ubuntuforums.org/showthread.php?t=66506") i got the following error message (i can't remember exactly which command gave me the information):
error setting MTRR (base = 0xe8000000, size = 0x01fd0000, type = 1) Invalid argument (22)
5659 5474

Then i found this bugreport: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/274045](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/274045) (in which the error is mentioned)

So i modified my xorg.conf file and now it looks like:
```

Section "Device"
        Identifier "Configured Video Device"
        Option "UseFBDev" "true"
        Driver "vesa"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
        Option "DPMS"
        HorizSync 28-51
        VertRefresh 43-60
        ModeLine "1024x768" 113.31 1024 1096 1208 1392 768 769 772 814 -HSync
EndSection

Section "Screen"
        "Default Screen"
        "Configured Monitor"
        "Configured Video Device"
EndSection

```

Now i can start ubuntu and login and work on it. However the screenresolution is wrong (it is a wide-screen), and i can't enable Compiz. Any ideas what my next steps could be to completely fix this issue?

thx!

---

### Post by teranex on 2008-12-03
To add some more info:

My system is completely up-to-date as i did a netboot installation with a direct connection to the internet to download the packages and i also checked it to be sure using the update manager.

I have friend who has the exact same laptop and he doesn't have this problem. However he did have a problem with ACPI, which he had to disable using a kernel parameter.

The video card of the laptop is a ATi mobility Radeon 9700 (RV350 [Mobility Radeon 9600 M10]) 64 Mb VRAM 

Could somebody help me with this please?

---

