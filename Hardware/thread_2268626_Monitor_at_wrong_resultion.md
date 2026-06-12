---
title: "Monitor at wrong resultion"
date: 2015-03-10
forum: Hardware
---

### Post by thomas29 on 2015-03-10
Hi,

First some description:
I'm running a dual Monitor setup with ubuntu 14.04 with 2 identical Monitors. In addition, I have a KVM switch running to switch between a laptop workstation and the desktop. 
To use the switch with my Desktop I have to employ an active converter for DVI -> DP conversion and this is where my issues probably are.
The Graphics card is an nvidia quadro K420 and I'm running the nvidia drivers at version 340.76

When everything is set up my first Monitor (running over the DP Port and KVM) works without issues. It is detected correctly as a Dell 24" with a resolution of 1920x1080.
For the second monitor (running over the active converter and KVM) I only get a choice of 2 different resolutions. One at 1280x720 and one unusable at 1920x1200.
I can run it with the 1280 resolution but it is a waste.
Now I have read a lot about xrandr and adding a new mode to the correct output. 
However whenever I try to do so, I get the following error:

```

cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

xrandr --output DVI-I-1 --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

xrandr --addmode DVI-I-1 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38
```

I have tried fiddling around with config files but not getting any success (and I still don't really get, how I can add resolution information to a specific monitor or output of the graphics card). Personally I got the impression that the config files were mostly ignored. 

Trying to force it to the resolution leads to more errors

```
# xrandr --output DVI-I-1 --fb 1920x1080 
xrandr: specified screen 1920x1080 not large enough for output DVI-I-1 (1920x1200+1920+0)
xrandr: Configure crtc 1 failed
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  21 (RRSetCrtcConfig)
  Value in failed request:  0x0
  Serial number of failed request:  48
  Current serial number in output stream:  48

```

the output I get from xrandr is as follows:

```
# xrandr
Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1280x720+1920+0 (normal left inverted right x axis y axis) 603mm x 342mm
   1920x1200      60.0 +   59.9  
   1280x720       60.0*    60.0     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 527mm x 297mm
   1920x1080      60.0*+
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
  1920x1080R (0x30d)  138.5MHz
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1083 end 1088 total 1111           clock   59.9Hz
  1920x1080_60.00 (0x30e)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz
  1920x1080_2 (0x30f)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz


```

I'm really at a loss at the moment. My current assumption is that I just don't get the setup of xorg.conf files and which files to modify to get this set up properly.

Any help would be appreciated.

---

### Post by thomas29 on 2015-03-12
I figured out one way to get the image to the "correct" resolution:
xrandr --output DVI-I-1 --scale 1.5x.1.5

However since this is oviously just scaling the output pixels, the whole image is blurry and thus useless.

What I don't get is why xrandr can scale the image to this resolution but not just force the graphics card to provide this resolution.
So I'm still hoping for some hints.

---

### Post by tgalati4 on 2015-03-12
What is the model of the KVM?  What are the supported resolution specifications for this KVM?

---

### Post by thomas29 on 2015-03-13
Hi
I don't think the KVM is the issue.
Its a StarTech SV231DPDDUA. 
And it works fine with the Monitor connected to it via the DP Port of my graphics card, transmitting the correct EDID and everything.
The issue seems to be, that the HDMI->DP Converter seems not to forward EDID information and instead gives some information itself that imply that only 1280x720 and 1920x1200 are possible.
The manufacturer claims, that the HDMI->DP converter supports anything up to 1920x1200 (including 1920x1080).
What I would like to do is to tell the graphics card that it should completely ignore any information gathered from the DVI Port and just send a signal to that port that's at 1920x1080.
And it should do so regardless on what monitor is connected (since it detects the Converter as monitor and that seems to not transmit the EDID information but instead sends it's own EDID info block).
If the converter can't cope with it, I know, that I have to ditch it and look either for another converter entirely or for some other way but I would at least like to give it a try.

---

### Post by thomas29 on 2015-04-08
Hi again.
I still haven't found a solution to this issue. I tried to set everything in xorg.conf but the files seems to be largely ignored by the nvidia drivers. 
I even tried to directly set the EDID information but that did not work neither.
here is an excerpt of my xorg.conf, maybe someone sees a mistake... 
```

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL P2414H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "MDP P2414H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K420"
EndSection

Section "Screen"

# Removed Option "metamodes" "DVI-I-1: 1920x1080 +1920+0, DP-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "DVI-I-1: nvidia-auto-select +1920+0, DP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "CustomEDID" "DFP-0:/etc/X11/edid.bin, DFP-2:/etc/X11/edid.bin"
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DVI-I-1: 1920x1080_60 +1920+0, DP-1: 1920x1080_60 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Keith_Helms on 2015-04-08
If I understand your configuration, you have a Ubuntu 14.04 desktop system with a nvidia quadro K420 video card which has one DVI and one Displayport output.   You have an active convertor attached to the DVI port to convert that into a 2nd displayport output and then you have both displayport outputs connected to a StarTech SV231DPDDUA KVM switch which has dual displayport video support.   Correct?  whew.

Just to try and eliminate the active convertor as a factor, what happens if you disconnect it from the KVM and connect it directly to one of the 2 monitors?  Do you get the correct video resolution, or does it still only offer the 2 incorrect resolutions?

---

### Post by thomas29 on 2015-04-09
To answer your question (assuming I got it right):
If I disconnect from the KVM (and just use DP Cable + ADAPTER + DVI Cable attached to the DVI out), I had the same issues, i.e. wrong EDID information provided by the adapter.

However I finally figured out my mistake in the xorg.conf file thanks to this post:
[http://askubuntu.com/questions/516946/configuring-multiple-monitors-to-use-custom-edids](http://askubuntu.com/questions/516946/configuring-multiple-monitors-to-use-custom-edids)

My mistake in the xorg.conf seems to have been:
a) To use , instead of ; to assign the 2 different costum edids
b) To have used DVI-I-1 // DP-1 in the metamodes line instead of DFP-0 and DFP-2 
c) To actually define the Modeline in the monitor settings and
d) add a couple of options (though I'm not entirely sure whether they are necessary but I wont try it without...


My working xorg.conf now looks like this:
```

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL P2414H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K420"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "ModeValidation" "AllowNon60hzmodesDFPModes, NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck, NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"
    Option         "metamodes" "DFP-0: 1920x1080 +1920+0, DFP-2: 1920x1080 +0+0"
    Option         "CustomEDID" "DFP-2: /etc/X11/edid.bin; DFP-0: /etc/X11/edid.bin"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I had a short look at the options. They are mainly to force the card to ignore whatever security checks normally used before transmitting the signal to avoid damage to the Monitor. So use this line with care and only if you are 100% sure, that your edid files are correct, since it could otherwise cuase damage to monitors that don't have internal options to handle wrong signals...

Anyways thanks for the efforts.

---

