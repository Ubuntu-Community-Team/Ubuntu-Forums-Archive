---
title: "Running Intel GPU &amp; Nvidia GPU triple monitor display"
date: 2014-06-15
forum: Hardware
---

### Post by Tayler_King on 2014-06-15
Hi there. I've been facing this issue for over a year now, and I have yet to fix it. I'm not too sure how.

I run an on-board Intel GPU along with a Nvidia GeForce 660. I also have three monitors.

With windows, I was able to run both graphics cards. Two displays off of the GTX, one off of the Intel. With Ubuntu, I don't know how to do this. I'm running 13.10 and it's a fresh install (I've installed about 50 versions today, still no success).

When I go into system details, here's the information I get for Graphics:
[IMG]http://i.imgur.com/7ks7c4z.png[/IMG]

Here's lshw -c video:
```

tayler@Ubuntu-Desktop:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: GK106 [GeForce GTX 660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

Here's xrandr:
```

tayler@Ubuntu-Desktop:~$ sudo xrandr
Screen 0: minimum 320 x 200, current 5040 x 1050, maximum 32767 x 32767
VGA1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected (normal left inverted right x axis y axis)
   1680x1050      60.0 +
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       70.0     60.0  
   1360x768       59.8  
   1152x864       70.0     60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DVI-D-1 connected 1680x1050+3360+0 (normal left inverted right x axis y axis) 433mm x 270mm
   1680x1050      59.9*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0     70.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8  
  1280x1024 (0x49)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x4a)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x4d)  108.0MHz
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1024x768 (0x51)   78.8MHz
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x53)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x55)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x56)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x57)   36.0MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x58)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x5a)   25.2MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x5b)   28.3MHz
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
  1680x1050 (0x5c)  119.0MHz
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1059 total 1080           clock   59.9Hz
  1152x864 (0x5e)  108.0MHz
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz

```

Any help's appreciated.

---

### Post by impliedconsent2 on 2014-06-15
I run the exact triple monitor setup - EXCEPT - I shut off the Intel 4600 graphics and run all 3 on the 660.  My guess is that you cannot do that because one of your monitors has a VGA connector and your MB supports (and "I think" 4000-series) the VGA.  So, my question - or - observation:  you are running 2 x monitors off the DVI-D and DVI-I and 1 x monitor off of Intel VGA.  On you 660, you still have 2 more ports available (or should) - HDMI and Displayport.  You could use an HDMI-->VGA adapator or DP-->VGA and run everything off the 660 (it has plenty + more power - I'm running 2 x 24" and 1 x 60") ... or ...

Drivers - I'm pretty sure that 13.10 has the working nouveau for Intel graphics and it should show up ... or ... update drivers direct from Intel to see if it can kick off. ( I think this is the link for your embedded graphics - if not - ya gotta search:  [https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+drivers&ProductProduct=3rd+Generation+Intel%c2%ae+Core%e2%84%a2+Processors+with+Intel%c2%ae+HD+Graphics+4000&ProdId=3712&LineId=1100&FamilyId=39](https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+drivers&ProductProduct=3rd+Generation+Intel%c2%ae+Core%e2%84%a2+Processors+with+Intel%c2%ae+HD+Graphics+4000&ProdId=3712&LineId=1100&FamilyId=39)

Side note:  I have used both the Intel and 660 at the same time on 13.04, 13.10 and 14.04; however, my monitors are either DVI or HDMI - no VGA - so, my experience is limited.

---

### Post by markohrastovec on 2014-12-17
Hi,

I am trying to achieve the same. With the default settings it works out of the box for me. That means Ubuntu (14.10) is using intel driver for intel card and nouveau driver for NVidia card.

However, I have some problems. When I log in sometimes not all three monitors work. I have to log out and log in again and then it is OK. I have tried to use proprietary NVidia driver. With proprietary driver I have some problems. I can make two logical screens (Screen0 and Screen1). That means I get all three monitors working, but two on NVidia form one desktop and for the third I need to load separate windows manager. That means, mouse can move between all three screens, but windows can not be dragged between Screen0 and Screen1.

We have a lot of multiseat installations where separating screens is desirable. These installations are on CentOS but xorg.conf configuration settings are the same. I only didn't bother to mess with window managers in Ubuntu. In one case (Ubuntu) where I need all three screens to use the same desktop it does not work. I have tried to enable Xinerama on options, but in that case I get black screens on all three monitors. With Xinerama set to "0" I get all three working, but as I said the third one is separate desktop.

Here is the example of xorg.conf. Be carefull to get BusID options right. They can be found with command "lspci":
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig# nvidia-xconfig:  version 331.113  (buildmeister@swio-display-x64-rhel04-03)  Mon Dec  1 21:15:34 PST 2014


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@roseapple)  Mon Feb  3 15:07:22 UTC 2014


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP LP2065"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection


Section "Monitor"


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP LP2065"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:01:00:0"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "intel"
    VendorName     "Integrated adapter"
    BoardName      "Intel"
    BusID          "PCI:00:02:0"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "VGA-0: nvidia-auto-select +1600+0, DVI-I-1: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

