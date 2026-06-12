---
title: "How to install Dell 4K display"
date: 2021-10-22
forum: Hardware
---

### Post by satimis on 2021-10-22
Hi all,

$ ubuntu-drivers devices```

== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==
modalias : pci:v000010DEd00002187sv00001462sd00003850bc03sc00i00
vendor   : NVIDIA Corporation
model    : TU116 [GeForce GTX 1650 SUPER]
driver   : nvidia-driver-470 - distro non-free recommended
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-460-server - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-460 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

$ sudo apt install nvidia-driver-470
[sudo] password for satimis: ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-driver-470 is already the newest version (470.63.01-0ubuntu0.20.04.2).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Settings -> Display
Resolution 1920 x 1080   (max)

Please help.  Thanks in advance

Regards

---

### Post by TheFu on 2021-10-25
Does **xrandr** show 4k resolutions as possible? Running it without any arguments should show a list of available resolutions. If it doesn't, you might need to get correct EDID data for the monitor to convince the GPU that other resolutions are possible.  I would expect a Dell 4K monitor to provide correct EDID, but if there is a KVM switch or some other adapter between the monitor and GPU, that could be blocking the information.  

I have a 4K 4x2 matrix HDMI switch that blocks the monitor's EDID information. This HDMI switch has toggle switches to force specific resolutions to be provided to GPUs. Alas I don't have a 4k screen, yet, so I cannot show that output. It also hides the vendor information for the monitor that the EDID data contains. To see human-readable EDID, use:
```
sudo get-edid | parse-edid
```

---

### Post by satimis on 2021-10-26
> **TheFu said:**
> Does **xrandr** show 4k resolutions as possible? R
-snip-
$ xrandr```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00* 

```
There are 2 SSD drives on this PC both running Ubuntu 20.00.  They are controlled by BIOS at booting.  This is a lately added SSD.  The 1st SSD is also running Ubuntu 20.04 without problem.

If rebooting this SSD and selecting on BIOS to boot the 1st SSD.  Ubuntu starts without problem running on 4K display.

It amazing me,

---

### Post by TheFu on 2021-10-26
uefi or legacy boot on both SSDs? Just asking to clarify.
My GT 1030 says this:
```
$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```
The DVI output goes into a DVI -to- VGA converter that only supports up to 1920x1200.  The get-edid|parse-edid doesn't see the Dell monitor - it only sees that converter device:
```
$ sudo get-edid |parse-edid 
...
Section "Monitor"
        Identifier "&#65533;."
        ModelName "&#65533;."
        VendorName "**AGO**"
        # Monitor Manufactured week 45 of 2013
        # EDID version 1.3
        # Digital Display
        DisplaySize 300 230
        Gamma 1.97
        Option "DPMS" "true"
        #Not giving standard mode: 1280x1024, 60Hz
        #Not giving standard mode: 1280x960, 60Hz
        #Not giving standard mode: 1280x800, 60Hz
        #Not giving standard mode: 1440x900, 60Hz
...
```

My xorg conf file is custom with lots of modelines created by some tools (sorry, I don't recall exactly how).  I override the edid it sees to use the edid for the Dell monitor:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "GeForce GT 1030"
    # Option "UseEDID" "False"
    Option "UseDisplayDevice" "DFP-0"
    Option "**CustomEDID**" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"
    # Option      "ModeDebug"
EndSection

```

I've been looking at 4K monitors and have updated some of my other equipment to handle that day. Perhaps this holiday season the prices will get into my budget?

I have zero idea to accomplish any of this using Wayland.

---

### Post by satimis on 2021-10-26
> **TheFu said:**
> uefi or legacy boot on both SSDs? Just asking to clarify.
My GT 1030 says this:
```
$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
- snip -

Hi,

Thanks for your advice.

Problem solved after running on Terminal;
$ sudo apt update
$ sudo apt dist-upgrade

$ sudo apt  upgrade didn't work.

$ xrandr[code]
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 697mm x 392mm
   3840x2160     60.00*+  29.98  
   2560x1440     59.95  
   2048x1280     59.96  
   2048x1080     24.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    23.98  
   1600x1200     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x720      59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-5 disconnected (normal left inverted right x axis y axis)

```

Now my problem gone.

I suppose the problem was caused on installing Ubuntu 20.04

Thanks again for your help.

Regards

---

### Post by TheFu on 2021-10-28
update/full-upgrade should be the first thing for any hardware related issues.
Add that to your troubleshooting checklist.

---

### Post by satimis on 2021-10-28
> **TheFu said:**
> update/full-upgrade should be the first thing for any hardware related issues.
Add that to your troubleshooting checklist.
Noted and thanks

Regards

---

