---
title: "Unable to Enable Vertical Sync in Catalyst Control Center"
date: 2015-01-15
forum: Hardware
---

### Post by 7achoneus on 2015-01-15
[COLOR=#2E3436][FONT=Open Sans]-Computer Specs-
Processor - 8x Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
Memory    - 16379MB (2893MB used)
Operating System - Kubuntu 14.10
Display-Resolution - 1920x1080 pixels
Display-Video Card        : AMD Radeon 6600M and 6700M 
SeriesVersion        : 4.4.12968 
Compatibility Profile Context 14.201.1006.1002
Direct Rendering        : Yes

[/FONT][/COLOR]Here is a capture of Catalysts Information section for reference if needed:
[IMG]http://williamthorup.com/000_Other%20Stuff/Ubuntu_Forums/catalyst_vsync_disabled_specs_1-15-15.jpg[/IMG]


I have been using the same AMD/Intel hybrid chipset for a couple years now, using both the open source and proprietary driver, and this is the first time I have encountered this.

[IMG]http://williamthorup.com/000_Other%20Stuff/Ubuntu_Forums/catalyst_vsync_disabled.jpg[/IMG]

Wait for verticle refresh is disabled without a checkbox to enable it, unlike in the past.  I don't recall Catalyst ever completely restricting this option.  

I was wondering if this might because I have never had much luck with getting full vertical sync on my ATI card over the last few years (Intel chipset works just fine), and now catalysts is smart enough to not give me the option, because it knows it won't work.  Or, there is something wrong with my install.  Here are the commands that I used to install, I am using the opensource driver, as I can't seem to get the latest proprietary driver to install anymore (funny because, in the past, it was the other way around).
```

sudo apt-get -y install fglrx fglrx-core fglrx-amdcccle fglrx-pxpress
sudo ln -svT /usr/lib /usr/lib64
sudo amdconfig --initial

```

I have fooled around with the vsync settings located under system settings>Desktop Effects>Advanced> to see if there was a conflict there that catalyst now detects.  No luck so far, also doesn't seem to affect vsync to much, regardless of what option combination I pick.

I have also ran this code with a reboot, no noticable change to vertical sync or to the option in Catalyst Control Center.
```

sudo aticonfig --sync-video=on --vs=on

OUTPUT:

Warning: Option 'TexturedVideoSync' doesn't affect running session.
Warning: Option 'Capabilities' doesn't affect running session.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-7

```

The reason why I think my driver install might be partially broken is because when I run this command it acts like that my device isn't listed in my xorg.conf.

```
aticonfig -info

OUTPUT:


No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.



```

When I open up my xorg.conf, I believe everything is there (I don't know for sure), and it looks like vertical sync is enabled with the option "TexturedVideoSync" being marked as "on".  Here is my xorg.conf.

```

Section "ServerLayout"
    Identifier     "amd-layout"
    Screen      0  "amd-screen" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "amd-monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection


Section "Device"
    Identifier  "intel"
    Driver      "intel"
    Option        "AccelMethod" "uxa"
    BusID       "PCI:0@0:2:0"
EndSection


Section "Device"
    Identifier  "amd-device"
    Driver      "fglrx"
    Option        "Capabilities" "0x00000800"
    Option        "TexturedVideoSync" "on"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "amd-screen"
    Device     "amd-device"
    Monitor    "amd-monitor"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```

As another note, this may have something to do with catalyst/ATIdriver breaking when I switch to my Intel GPU and rebooting, or not. After the switch to the Intel GPU, I am unable to switch back to the ATI GPU.  But that might be a topic for another thread.

Let me know if you need any logs, or need me to do anything for testing. I am more than willing, in order to find a solution to this vertical sync problem.

---

