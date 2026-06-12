---
title: "Using Intel Integrated Graphics alongside Nvidia GT 630"
date: 2016-05-04
forum: Hardware
---

### Post by Lucas_Lower on 2016-05-04
Hello,

I just recently installed Ubuntu 16.04. I've been using it just fine, the only issue is with the displays. What I am trying to do is run three displays on two separate video outputs, one the Intel Integrated Graphics on the motherboard, and the other an Nvidia GT 630. I have installed version 361 of the Nvidia drivers, and attempted to install the Intel drivers for 15.10 by changing the distribution file. It installed successfully, but did not seem to do anything. Here's the setup that I am on right now:

- 1 monitor on VGA from integrated graphics
- 1 monitor on DVI from Nvidia card
- 1 monitor on HDMI from Nvidia card

In BIOS, I have the "Intel Multi Monitor Feature" enabled, which meant in Windows that both outputs were recognized and could be configured. In Ubuntu, running "lshw -C video" gives me:

```
root@Lucas-PC:~# lshw -C video
  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 630]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:30 memory:fa000000-faffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

```

The Nvidia card is the only one being recognized. I've tried changing which monitors were plugged in where and how, with different results every time.
The first setup I tried was this:

- 1 monitor on VGA from Nvidia card
- 1 monitor on DVI from Nvidia card
- 1 monitor on VGA from integrated

This setup works under windows, but only shows 2 displays on Ubuntu. The weird thing is, when I run lshw on this one, it shows both the Nvidia card and the Intel integrated. It still only runs two monitors though, one from the Intel and one from the Nvidia.

The second setup that I tried was as follows:

- 1 monitor on VGA from integrated
- 1 monitor on HDMI from integrated
- 1 monitor on DVI from Nvidia

This one was the weirdest. lshw again recognized both. All three monitors displayed the desktop, but the resolution was very messed up to the point of being unusable. The nvidia monitor showed normal resolution, but was the sum of all three displays on the one display. When I would move the mouse to the right of the screen, it would slide over to show the other displays. The other two displays seemed very stretched, and the cursor did not line up correctly.

Any ideas on how to get this working?

Thanks,
Lucas

EDIT: Here is xrandr as well

```

root@Lucas-PC:~# xrandr
Screen 0: minimum 8 x 8, current 3520 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1600x900+1920+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900      60.00*+
   1280x800      59.81  
   1280x720      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  60.00    59.94    50.00    50.00    60.00    50.04  
   1920x1200     59.95  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       59.94    59.93  

```

And also xorg.conf. For some reason it was dated on the end like this: xorg.conf.05022016, just "xorg.conf" doesn't exist.

```

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

I have no idea how to setup xorg.conf so that may have something to do with it.

---

