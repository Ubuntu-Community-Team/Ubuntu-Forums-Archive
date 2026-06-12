---
title: "external screen connected but blank"
date: 2018-09-05
forum: Hardware
---

### Post by damndecentdave on 2018-09-05
Installed lubuntu 18.04 i386 to an older laptop that was running windows 10 and I am greatly impressed with it's new lease on life! Only real issue I have is I'm unable to get the external monitor working. Xrandr shows both LVDS (primary) and VGA-0 connected.
~$ xrandr
Screen 0: minimum 320 x 200, current 2480 x 1050, maximum 8192 x 8192
VGA-0 connected 800x600+1680+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02 +  75.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00*   60.32  
   640x480       75.00    59.94  
   720x400       70.08  
LVDS connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050     60.00*+
   1400x1050     60.00  
   1280x1024     59.95  
   1440x900      59.99  
   1280x960      59.99  
   1280x854      59.95  
   1280x800      59.96  
   1280x720      59.97  
   1152x768      59.95  
   1024x768      59.95  
   800x600       59.96  
   848x480       59.94  
   720x480       59.94  
   640x480       59.94  
S-video disconnected (normal left inverted right x axis y axis)

The graphics card is a ATI Mobility Radeon x1400 (RV515 chipset) and there are no errors in the /var/log/xorg.0.log file. lshw -c identifies the VGA controller as RV515/M54 and the driver as "radeon".
~$ lshw -c video           
       description: VGA compatible controller
       product: RV515/M54 [Mobility Radeon X1400]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:d0000000-dfffffff ioport:ee00(size=256) memory:efdf0000-efdfffff memory:c0000-dffff

I am able to drag windows across to the VGA screen but can't see them (all blank). the VGA menu screen says it's in Power Save mode which I think means it is getting no signal. The VGA screen and monitor work when plugged into a different lubuntu PC and I've closely inspected the cable connections. I'm thinking that maybe the video card is kaput!  Any help is appreciated.

---

### Post by hometow1 on 2018-09-05
When an external monitor is connected to a laptop, the login screen is only displayed on the internal one and in some case is not visible (1723025)

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Known_issues](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Known_issues)

---

### Post by damndecentdave on 2018-09-05
hometow1, thanks but the issue is not the fact that I can't see the login screen which indeed comes up on the laptop screen. I can login and the system comes up OK. So, I have full functionality on the laptop screen but the external monitor is blank. I can drag images off the right hand edge of the laptop but the external monitor which is configured to be to the right of the laptop screen remains blank throughout.

---

