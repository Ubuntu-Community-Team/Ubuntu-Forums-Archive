---
title: "Ubuntu 16.04 Display on Multiple Monitor Error"
date: 2016-11-21
forum: Hardware
---

### Post by ph423 on 2016-11-21
Hello to the Community!

I want to setup my laptop to have two external displays (3 total), but unfortunately I encounter errors. After some research, it seems that no solution has been found, and thus here I am.

Here's the problem:

The Screen Display menu recognizes the presence of both external monitors, but automatically disables one of the two. When the screen is considered as disabled, it is very hard/buggy to drag screens around in the display menu. The disabled screen can be enabled; doing so eases the drag/drop of the screen positions. However if the disabled screen is activated and the changes are applied, the previously enabled screen (the one that was working) is disabled and the screen positions become all messed-up (often overlapping).

I often get an error message, either `GDBus.Error: org.gtk.GDBus.UnmappedGError.Quark._gsd_2drr_2derror_2dquark.Code2: could not set the configuration for CRTC 97` or `could not set the configuration for CRTC 97` or `could not set the configuration for CRTC 96`.

Here's a screenshot:

[IMG]https://s17.postimg.org/tbbheoxtr/Selection_024.png[/IMG]

Here's my setup:

Ubuntu 16.04 LTS 64 bits
Lenovo Thinkpad T430s
Processor Intel Core i5-3230M
Graphics: 
- Intel Ivybridge Mobile (as primary)
- NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]

xrandr output:
```

Screen 0: minimum 8 x 8, current 3200 x 1200, maximum 32767 x 32767
LVDS1 connected primary 1600x900+0+300 (normal left inverted right x axis y axis) 309mm x 174mm
   1600x900      59.98*+
   1440x900      59.89  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   800x450       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 connected (normal left inverted right x axis y axis)
   1280x1024     60.02 +  75.02  
   1152x864      75.00  
   1024x768      75.08    75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 connected 1600x1200+1600+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200     60.00*+
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



```

`lshw -c video` output:
```

  *-display               
       description: 3D controller
       product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:6000(size=64)

```

`lspci | grep VGA` output:
```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

There is a similar bug reported [here]("https://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg463794.html"), and an outdated solution to the same problem [here]("https://ubuntuforums.org/showthread.php?t=1835391").

Any idea what could be done to solve this issue?
Do you think switching the VGA compatible controller for the NVIDIA card controller would be a possible solution?

Let me know what you have in mind!
Cheers

---

### Post by ph423 on 2017-03-09
I stumbled upon the issue once again, and after some more research I found out this feature (multimon) had been[ removed from the Lenovo T430s laptop alongside some other models.]("https://blogs.technet.microsoft.com/keithcombs/2012/11/15/multiple-monitors-multimon-with-the-lenovo-thinkpad-t430s/") This can be circumvented by adding a lenovo dock, and even then requires some bodge to work. I will close this thread as [SOLVED] due to the unsolvability of the said issue without external peripherals.

Cheers!

---

