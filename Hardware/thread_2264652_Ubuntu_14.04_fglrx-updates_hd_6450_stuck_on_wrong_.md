---
title: "Ubuntu 14.04 fglrx-updates hd 6450 stuck on wrong resolution"
date: 2015-02-09
forum: Hardware
---

### Post by pepsifx357 on 2015-02-09
Believe me I know there enough threads out there on this very subject.  I've gone through every single one of them.

Here's my issue.  I've got a vga passthrough thing going on with kvm so I've got an nvidia gtx 560 just passing through, if that matters, and an ATI radeon hd 6450 on the host machine.  I've had this card for a couple of weeks now and it has yet to make it past 1600x1200.  I need it to be 1680x1050.  I tried the open source radeon driver and it doesn't seem to even want to load. 640x480 is pretty tought to work with.  I tried to modprobe it and it couldn't find the radeon driver at all.  The package I installed for it was xserver-xorg-video-ati, and nothing.  I don't know why it wouldn't load on boot.  I've checked and rechecked all my blacklistings and radeon is not being blacklisted.  So i went back to the fglrx driver.  I'm damned if I do and damned if I don't here.  I've litteraly gone through about two or three pages of google searches trying to find a solution.  I've run out of solutions to try.  The only thing I really havent tried yet is xrandr, but I have no idea how to use it.  I've edited the xorg.conf file.  Tried amdcccle, with sudo.....I don't know why this thing won't just use the right resolution.  I don't know if this makes any difference or not, but the monitor is connected via VGA cable, since the DVI source is being used by the Nvidia card being passed through.

Here's xrandr's output

```
ben@KVM-Host:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 16384 x 16384
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected primary 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9
```

Here's the xorg.conf file that aticonfig -initial made

```
Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Monitor"
        Identifier   "0-CRT1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1600x1200"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-CRT1" "0-CRT1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I really would appreciate some help on this one, my eyes are straining to write this because of it being so blurry.

Thanks.

---

### Post by pepsifx357 on 2015-02-11
bumpity

---

### Post by Jim_Lawrence on 2015-02-11
As you can see from the output of your above xrandr, the connected primary is CRT1. 

To confirm this, you can run 

xrandr | grep "connected primary"

now enter

cvt 1680 1050 60 

you should get an output like 

 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

now type 

xrandr --newmode 1680x1050 146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

copy/paste the tail end of the output from the cvt command after Modeline "1680x1050_60.00"

now type 

xrandr --addmode CRT1 1680x1050

now type

xrandr --output CRT1 --mode 1680x1050

That should do it.

---

### Post by pepsifx357 on 2015-02-14
Thank god for you jim!!!!!!!!!!!!

I can see again!

---

