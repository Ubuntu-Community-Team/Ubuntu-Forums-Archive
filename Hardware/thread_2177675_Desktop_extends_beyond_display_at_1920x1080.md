---
title: "Desktop extends beyond display at 1920x1080"
date: 2013-09-29
forum: Hardware
---

### Post by twjohnso on 2013-09-29
I have Ubuntu 13.04, 32bit (though this happened with 12.04 and 12.10.)  When I first install it and log in under my profile, it screen looks just fine.  After awhile (perhaps a package or changed setting, I can't figure out which/how) the screen changes such that the edges of the desktop extend beyond the edges of my TV and are cropped off (the task bar on the left and the notification bar along the top.)  

However, the login and guest profile screens look fine (they may be at a different resolution/setting?)  Yet, the Grub and Terminal (CTRL+ALT+F2) windows are also cropped.

```
Following the suggestion of other posts and articles found, I checked the output of xrandr...
HDMI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 1039mm x 584mm
   1920x1080      60.0 +   24.0  
   1920x1080i     30.0 +
   1680x1050      59.9  
   2880x480       59.9  
   2880x480i      30.0  
   1280x1024      60.0* 
   1440x900       59.9  
   1280x720       60.0  
   1024x768       60.0  
   1440x480       59.9  
   1440x480i      30.0     30.0  
   800x600        60.3  
```

I found the Intel driver installer and used that (hoping to get better results if it was a driver issue).  My video card is listed as...
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0493
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at e1400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
```

Trying the various options in display settings, I get the following results...
[TABLE="class: grid, width: 500"]
[TR]
[TD="align: center"]**Setting**[/TD]
[TD="align: center"]**Result**[/TD]
[/TR]
[TR]
[TD]1920x1080 (16:9)[/TD]
[TD]Outter edges cropped (task bar and notification bar)[/TD]
[/TR]
[TR]
[TD]1680x1050 (16:10)[/TD]
[TD]TV says no signal, times out and reverts to previous setting[/TD]
[/TR]
[TR]
[TD]1440x900 (16:10)[/TD]
[TD]Everything fits on screen, desktop too small[/TD]
[/TR]
[TR]
[TD]1280x1024 (5:4)[/TD]
[TD]Everything fits on screen, looks stretched[/TD]
[/TR]
[TR]
[TD]1280x720 (16:9)[/TD]
[TD]Outter edges cropped (task bar and notification bar, area is too small to display all the windows that were open)[/TD]
[/TR]
[TR]
[TD]1024x768 (4:3)[/TD]
[TD]Everything fits on screen, desktop too small[/TD]
[/TR]
[TR]
[TD]800x600 (4:3)[/TD]
[TD]Didn't bother trying[/TD]
[/TR]
[/TABLE]

Any ideas why 1920x1080 won't work? I noticed in Win7 that it does the same thing (trims off the edges, it runs at 1440x900.)

---

